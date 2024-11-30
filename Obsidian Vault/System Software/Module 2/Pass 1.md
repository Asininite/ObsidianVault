- assign addresses to all statements
- save addresses to the labels for use in pass 2
- process some assembler directives like RESW and BYTE

```
begin

    read first input line

    if OPCODE = 'START' then

    begin

        save #operand as starting address

        initialize LOCCTR to starting address

        write line to intermediary file

        read next input line

    end {if START}

    else

        initialize LOCCTR to 0

        while OPCODE != 'END' do

        begin

            if this is not a comment line

            begin

                if there is symbol in LABEL field then

                begin

                    search SYMTAB for LABEL

                    if found then

                        set error flag (duplicate symbol)

                    else

                        insert (LABEL, LOCCTR) into SYMTAB

                end (if)

                search OPTAB for OPCODE

                if found then

                    add 3 * (instruction length) to LOCCTR

                else if OPCODE = 'WORD' then

                    add 3  to LOCCTR

                else if OPCODE = 'RESW' then

                    add 3 * #OPERAND TO LOCCTR

                else if OPCODE = 'RESB' then

                    add #OPERAND to LOCCTR

                else if OPCODE = 'BYTE' then

                begin

                    find length of constant in bytes

                    add length to LOCCTR

                end {if BYTE}

                else

                    set error flag {invalid operation code}

            end {if not a comment}

            write line to intermediary file

            read next input line

        end {while not END}

    write last line to intermediary file

    save LOCCTR - starting address as program length

end {pass 1}
```