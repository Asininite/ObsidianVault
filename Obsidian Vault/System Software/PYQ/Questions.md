ALPHA RESF 1    ; Reserve one floating-point word for ALPHA
BETA  RESF 1    ; Reserve one floating-point word for BETA

; ... (other code) ...

LDA BETA       ; Load BETA
MUL #4         ; Multiply by 4
SUB #9         ; Subtract 9
STA ALPHA       ; Store the result in ALPHA

; ... (rest of the program) ... 