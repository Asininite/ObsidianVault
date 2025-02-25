
![Preview image](https://miro.medium.com/v2/resize:fit:700/0*-z6rU1KaEpJOS4A9)

# How to Analyze Heartbeats in 15 Minutes in Python

## Analyze electrocardiograms (EKGs) and find possible arrhythmias with code. (This article is for educational purposes only.)

[![Proto Bioengineering](https://miro.medium.com/v2/resize:fill:88:88/1*dJo9fkv0fzln2cQft1m9dQ.png)

](https://medium.com/@protobioengineering "Learn to code for science. “Everything simple is false. Everything complex is unusable.” — Paul Valery")

[Proto Bioengineering](https://medium.com/@protobioengineering "Learn to code for science. “Everything simple is false. Everything complex is unusable.” — Paul Valery")[Follow](https://medium.com/@protobioengineering "Learn to code for science. “Everything simple is false. Everything complex is unusable.” — Paul Valery")

October 6, 2024 (Updated: October 26, 2024)

You may have the seen the little blip above in a TV show, in the hospital, or on your smart watch. But what does it mean? Isn't it just a random squiggly line that shows the chaotic electricity of a single heartbeat?

**There are actually 100s of pieces of information about the heart buried in this squiggly line,** based on how it is shaped and how all of the bumps are spaced out in relation to each other. We are going to talk about what all of these bumps and curved lines (or "waves") mean and then cover how to automate their analysis with Python code and [SciPy](https://scipy.org/).

### Disclaimer: DANGER!

**This article is for educational purposes only.** Neither the following code nor this tutorial are approved by the [FDA](https://www.fda.gov/) nor by any governing body to diagnose heart-related medical issues or any other medical issues. Nothing in this article constitutes medical advice.

DO NOT use the code nor information contained in this article to diagnose yourself or any other person or living thing with a medical issue. **Do not use the code or information in this article to make medical decisions for yourself or others.** This article was not written by a licensed physician.

**If you have any medical concerns, please consult a licensed physician.** If you are concerned that you or another person are experiencing a medical emergency, please go to your nearest hospital's emergency department immediately or call 911 (or [your region's equivalent emergency number](https://travel.state.gov/content/dam/students-abroad/pdfs/911_ABROAD.pdf)).

The misuse of the information and code in this article can result in **SERIOUS INJURY OR DEATH**.

### Electrocardiograms: What Are We Really Looking at?

![None](https://miro.medium.com/v2/resize:fit:700/1*mDoZ39s9Lqe25jG0yxykOA.jpeg)

A [normal](https://www.uptodate.com/contents/normal-sinus-rhythm-and-sinus-arrhythmia) electrocardiogram (EKG) with 5 heartbeats (graphic by [Andrewmeyerson](https://commons.wikimedia.org/wiki/File:Normal_Sinus_Rhythm_Unlabeled.jpg) on Wikimedia Commons).

When we are looking at heartbeats on a smart watch or on a heart monitor, what does the jagged line actually mean? It may seem like a chaotic squiggle, but each millisecond and millimeter of that line can tell us specific things about the heart.

Above is an **electrocardiogram** (or **EKG** or **ECG**). An [electrocardiogram](https://www.mayoclinic.org/tests-procedures/ekg/about/pac-20384983) is a graph of the heart's electrical signal over a few seconds (or minutes). Doctors, nurses, and paramedics use these to make sure your heart is pumping with the correct strength and timing.

#### Main parts of the EKG

**Each big spike above is one heartbeat** — that much is obvious — but what other information could possibly be in there?

There are **three big waves** in each heart beat that you see above. A little bump, a big spike, then a little bump again. These show, in order:

1. the **atria pumping** (bump 1)
2. the **ventricles pumping** (the big spike, or bump 2)
3. the **heart resetting** (bump 3)

![None](https://miro.medium.com/v2/resize:fit:700/1*9G4SGUTd-0fOXh-CTxAl2A.png)

A single heartbeat from an EKG. Each wave has a name from P-T in the alphabet. Illustrated by [Agateller](https://en.wikipedia.org/wiki/User:Agateller) on [Wikipedia](https://en.wikipedia.org/wiki/QRS_complex).

The **first small bump** is called the "P wave," the **big spike** is the "QRS complex," then the **third bump** is the "T wave". It is a little more complicated than that, but this is the gist of what we're looking at.

**The point of the EKG** is to make sure that all of these parts are squeezing in unison with the **correct timing and order**. Any deviations to the timing and order mean something is wrong. This could be something as simple as a person being a little anxious or having low electrolytes, or it could mean something very wrong is happening, like a heart attack.

### Some Quick Examples of "Bad" EKGs

Here is how the EKG might change when things go wrong. When a doctor or paramedic uses the word "arrhythmia," this is the type of thing they're talking about.

Notice how some parts of the EKG stay the same while others differ. These changes indicate that certain steps in the heartbeat are not happening in the correct sequence, which we'll discuss below.

![None](https://miro.medium.com/v2/resize:fit:700/1*dVmssLBaWAtBPj_AbZ-csQ.png)

This EKG shows too many waves in between the R waves. This creates a ["sawtooth" appearance](https://www.hopkinsmedicine.org/health/conditions-and-diseases/atrial-flutter).

![None](https://miro.medium.com/v2/resize:fit:700/1*RuaqRZTo1oVhyYpH0idnbQ.png)

One of the types of "heart blocks," where a P wave is not always able to kick off a full heartbeat. Some P waves appear but without a QRS complex following them.

![None](https://miro.medium.com/v2/resize:fit:700/1*XQp3QyPJeSkk5x1S9CSguQ.png)

A particularly deadly type of heart attack. Here, the ST segment is several boxes above the baseline, indicating an issue with ventricular conduction and/or contraction.

Again, please **DO NOT use this information to make medical decisions for yourself or others.** Please consult a licensed physician about any medical concerns, or visit your nearest emergency department, or call 911 or [your region's equivalent emergency number](https://travel.state.gov/content/dam/students-abroad/pdfs/911_ABROAD.pdf) if you are experiencing a medical emergency.

### Back to the Heart

There are **4 chambers** in the heart. The top 2 are the **atria** and the bottom 2 are the **ventricles**. These need to **squeeze in sync with each other** in order to have a healthy heartbeat.

Both of the atria pump at the same time, then both of the ventricles pump at the same time right after that. The heart does this in order to multi-task. That way, there aren't 4 separate contractions for each chamber — only 2.

![None](https://miro.medium.com/v2/resize:fit:700/1*qC11WCgh9o3uuDP7vF-85Q.png)

The hearts 4 internal chambers (the 2 atria and the 2 ventricles) as illustrated by [Wapcaplet](https://en.wikipedia.org/wiki/User:Wapcaplet) on [Wikipedia](https://en.wikipedia.org/wiki/Heart).

The reason for having two atria and two ventricles is that they each handle different parts of blood flow to and from the lungs. The **right atria** and **right ventricle** take in deoxygenated blood ("used" blood) from the body and pump it to the lungs to get re-oxygenated. The **left atria** and **left ventricle** then take in oxygenated blood that just returned from the lungs and pump it back out to the rest of the body.

![None](https://miro.medium.com/v2/resize:fit:700/1*BkGifyyiT9IbKJmKCjbD6A.png)

(Graphic derived from [Wapcaplet](https://en.wikipedia.org/wiki/User:Wapcaplet)'s heart illustration on [Wikipedia](https://en.wikipedia.org/wiki/Heart))

Note that right and left are switched in medical images, because we always talk about [the](https://www.dummies.com/article/academics-the-arts/science/anatomy/standard-anatomical-position-240458/) _[patient's](https://www.dummies.com/article/academics-the-arts/science/anatomy/standard-anatomical-position-240458/)_ [right and left](https://www.dummies.com/article/academics-the-arts/science/anatomy/standard-anatomical-position-240458/).

#### The left vs. the right side of the heart

To reiterate, the big differences between the left and right side of the heart are:

- where they're **getting blood from**
- where they're **sending it to**
- whether that blood is **deoxygenated** or has just been **reoxygenated** by the lungs

#### The "reset"

The third bump on the EKG (the "T wave") is the ventricles resetting. By "reset" we mean an electrical and chemical reset, where everything [repolarizes](https://www.ncbi.nlm.nih.gov/books/NBK537194) from bottom of the heart upward to prepare for the next heartbeat. In the body, electrical signals get sent by a sort of chemical domino effect, called an [action potential](https://www.ncbi.nlm.nih.gov/books/NBK538143), and these dominoes need to be reset after each [contraction](https://www.webmd.com/fitness-exercise/types-of-muscle-contractions).

On the EKG, we can only see the ventricles resetting with our own eye, which we call the "**T wave**." The atria _also_ reset after they fire, but this reset is overshadowed by the giant voltage change of the QRS complex.

![None](https://miro.medium.com/v2/resize:fit:700/1*9G4SGUTd-0fOXh-CTxAl2A.png)

The atria's reset would show a wave on the EKG if the R wave wasn't occurring at the same time and overshadowing it. Illustrated by [Agateller](https://en.wikipedia.org/wiki/User:Agateller) on [Wikipedia](https://en.wikipedia.org/wiki/QRS_complex).

### Starting to Interpret the EKG

That sounds simple enough. **Where is all the "information" embedded into these 3 peaks then?**

**The information is in 5 things:**

1. the **height** of the peaks
2. the **width** of the peaks
3. the **peaks' distances** from each other
4. the height of the **lines in between** the peaks
5. that **the peaks are present** to begin with

![None](https://miro.medium.com/v2/resize:fit:700/1*bsBvwREvxN_5RkxH44wH-g.png)

The values of each box on an electrocardiogram's grid. Illustrated by Vicente Alarcon-Aquino in [Starostenko et al. (2015)](https://www.researchgate.net/publication/278682017_Remote_HealthVital_Sign_Monitoring).

When peaks are:

- too **short/tall**
- too **narrow/wide**
- too **far apart**
- or **aren't even visible** on the EKG

Then the patient may have a [problem](https://www.nhlbi.nih.gov/health/arrhythmias). There are a [couple hundred different types](https://litfl.com/ecg-library/diagnosis/) of these problems, which we call "[arrhythmias](https://www.nhlbi.nih.gov/health/arrhythmias)" (literally meaning "bad rhythms").

By learning what the heights and widths of all of these lines are supposed to be in a healthy heart, we can start to identify [some of the most common and deadliest arrhythmias](https://litfl.com/killer-ecg-patterns-part-1/) in supposedly unhealthy hearts.

> Please remember that this article is for educational purposes only. Do not diagnose yourself or another person with an arrhythmia or any other medical condition. Please see a licensed physician for any medical concerns. Call 911 if you believe you are experiencing a medical emergency.

Considering that EKGs are just [digital signals](https://medium.com/@protobioengineering/digital-signals-for-idiots-part-1-what-is-digital-signals-processing-fc9ae9a72c03) and that identifying anomalies in EKGs is about _measuring things_, you may already be brainstorming **how you can do this in your code**. As a preview, our Python code will partly involve finding peaks in the EKG with [NumPy](https://numpy.org/) and [SciPy](https://scipy.org/) and then labeling and visualizing these peaks with [Matplotlib](https://matplotlib.org/).

**If you're new to NumPy, SciPy, and other libraries, we will make the introduction easy.**

If you're already familiar with SciPy, its built-in `find_peaks()` function will come in handy by helping us make the graph below. ([SciPy documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.find_peaks.html))

![None](https://miro.medium.com/v2/resize:fit:700/1*Lav_3eHamzxG_0VfwJsw2Q.png)

The code in [our EKG article series](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4) will help you identify and label all of the PQRST waves and make the graph above. Read below for a preview of this code!

We will also touch on how traditional [DSP](https://medium.com/@protobioengineering/list/digital-signal-processing-dsp-in-python-012629adec83) techniques and machine learning are helpful — or not so helpful — for EKGs later in our [EKG series](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4).

### What is with the red grid?

The red grid that EKGs get printed on helps doctors measure an EKG quickly with their own eyes. All EKG paper comes with a pre-printed grid like this.

![None](https://miro.medium.com/v2/resize:fit:700/1*bsBvwREvxN_5RkxH44wH-g.png)

The values of each box on an electrocardiogram's grid. Illustrated by Vicente Alarcon-Aquino in [Starostenko et al. (2015)](https://www.researchgate.net/publication/278682017_Remote_HealthVital_Sign_Monitoring).

The grid's boxes are equal to an exact amount of **time** and **voltage**. **1 red box** is **0.04 seconds** in width and **0.1 mV** in height. When medical providers read an EKG, they have already memorized how many milliseconds everything is supposed to be in a healthy heartbeat, so they can just look at the EKG and say, "That P wave is 2.5 boxes wide, which means it was 0.1 seconds long. Good!" And so on.

### How short, tall, or narrow is everything supposed to be?

Before we get the urge to throw the EKG into a machine learning algorithm, know that this is a [well-researched](https://www.ncbi.nlm.nih.gov/books/NBK549803/) part of cardiology.

Each part of the EKG has a [known range of how many milliseconds long](https://litfl.com/ecg-rate-interpretation/) that it is supposed to be in the average healthy person ([with some caveats](https://www.faa.gov/pilots/safety/pilotsafetybrochures/media/NormalVariant_JobAid_508.pdf)). As we mentioned, medical providers memorize these ranges and then read patients' EKGs with their own eyes in seconds flat.

Here are some basic values from [Life in the Fast Lane](https://litfl.com/ecg-rate-interpretation/):

- **QRS complex**: 2–3 boxes (0.08–0.12 seconds)
- **PR interval**: 3–5 boxes (0.12–0.20 seconds)
- **P wave**: X-Y milliseconds long (X-Y boxes)
- **R wave**: around [6 boxes tall](https://www.sciencedirect.com/topics/nursing-and-health-professions/r-wave) (0.6 mV)
- The **ST segment** should be less than [~0.1 mV above baseline](https://www.ncbi.nlm.nih.gov/books/NBK532281)

There are dozens of other things to measure, but this is a start.

If you're more of a qualitative thinker, check out [this list of things to look for in PQRST waves](https://litfl.com/ecg-rhythm-evaluation/).

(**Additional sources:** [1](https://www.ncbi.nlm.nih.gov/books/NBK551635/), [2](https://www.nottingham.ac.uk/nursing/practice/resources/cardiology/function/normal_duration.php), [3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1122394/))

### Getting Started with Python

This will be a quick introduction to opening, reading, and labeling an EKG.

**To start analyzing EKGs we need the following:**

- [A digitized EKG](https://www.kaggle.com/datasets/protobioengineering/mit-bih-arrhythmia-database-modern-2023)
- Python
- SciPy, Pandas, Matplotlib, and NumPy (Python libraries)

We will then take the following steps.

#### Overall Steps

1. Download the EKG
2. Import our libraries into Python (SciPy, etc.)
3. Load the EKG into Python using Pandas
4. Plot the EKG with Matplotlib
5. Find the peaks of the R waves with SciPy
6. Graph the labeled R waves with Matplotlib

The [rest of our EKG series](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4) covers the other aspects of analyzing EKGs as well.

#### Step 0: Download the Python libraries

You will need Python and a few extra Python libraries to open and analyze the EKGs.

If you're well-versed in Python, run Pip to install the necessary libraries:

Copy`pip install scipy pandas numpy matplotlib`

If you're newer to Python, download Python 3 and all of the necessary libraries here:

- [Python 3](https://www.python.org/downloads/)
- [SciPy](https://scipy.org/install/)
- [NumPy](https://numpy.org/install/)
- [Pandas](https://pandas.pydata.org/docs/getting_started/install.html)
- [Matplotlib](https://matplotlib.org/stable/install/index.html)

#### Step 1: Download the EKG

You can download the famous **MIT-BIH Arrhythmia** dataset [from our Kaggle here](https://www.kaggle.com/datasets/protobioengineering/mit-bih-arrhythmia-database-modern-2023). You will get a set of 48 EKGs in CSV format.

We will use the first patient's EKG (`100.csv`) for this example.

#### Step 2: Import scientific libraries into Python

At the top of our [Python file](https://medium.com/@protobioengineering/how-to-make-a-standalone-python-script-44aa9b83ee26) or notebook, we import our libraries like so:

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt`

#### Step 3: Load the EKG into Python using Pandas

To load the EKG into our code, we will write:

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt  ekg = pd.read_csv('100.csv', index_col=0)`

`index_col=0` tells Pandas to use the first column from the CSV as the `index` or row numbers.

#### Step 4: Plot the EKG with Matplotlib

We can plot the EKG with a simple `plot()` function. However, the CSV has two columns, which represent two channels from the EKG. We'll go over what these channels mean in later articles.

Let's graph only the first column (or channel) from the EKG, which has the name of `MLII`:

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt  ekg = pd.read_csv('100.csv', index_col=0) ekg['MLII'].plot()`

This gives us the following graph:

![None](https://miro.medium.com/v2/resize:fit:700/1*1w7WaulG7BX13fenICeQUg.png)

This is ugly and indecipherable, since it's the full 30-minute EKG. Let's pare it down to the first few heartbeats by changing the code to:

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt  ekg = pd.read_csv('100.csv', index_col=0)  # Get the first 1000 data points from the EKG ekg_first_4_beats = ekg[0:1000]  # Plot the 'MLII' column from the EKG ekg_first_4_beats['MLII'].plot()`

Now the graph is:

![None](https://miro.medium.com/v2/resize:fit:700/1*J6_zUaf7sE9oydpkZrg3rA.png)

That looks more like we expected. We see 4 heart beats, which includes 4 big, R-wave spikes with some P, Q, S, and T waves on either side of them.

This graph is messier than the example graphics from above for two reasons. One, real life is messy and collecting digital signals from living things inevitably causes noise. Two, this person actually has an arrhythmia, but we will cover the identification and analysis of this in later articles.

#### Step 5: Find the peaks of the R waves with SciPy

SciPy can help us find any peaks and valleys in a digital signal with `find_peaks()`.

This is like the plotting code above, except we're just going to extract the `peaks` for now.

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt  ekg = pd.read_csv('100.csv', index_col=0) ekg_first_4_beats = ekg[0:1000]  # Find the peaks of the R waves peaks, metadata = scipy.signal.find_peaks(ekg_first_4_beats['MLII'], height=0.6)`

Above, we are finding all of the R waves in the graph (or the `peaks`) by calling `scipy.signal.find_peaks()` on the first 4 heartbeats from the EKG and telling `find_peaks()` that we only care about the peaks that are above a `height` of `0.6` on the Y-axis. Note that we only use the `MLII` column/channel from the EKG dataset, since the EKG has multiple channels of data.

Now, we have the locations of our R waves' peaks and we can graph them.

#### Step 6: Graph the R Waves with Matplotlib

To graph the R waves, we will first graph our heartbeats exactly as we did before, then we will plot little Xs on top of that graph.

Copy`import scipy import numpy as np import pandas as pd import matplotlib.pyplot as plt  ekg = pd.read_csv('100.csv', index_col=0) ekg_first_4_beats = ekg[0:1000]  # Find the peaks of the R waves peaks, metadata = scipy.signal.find_peaks(ekg_first_4_beats['MLII'], height=0.6)  # Graph the heartbeats ekg_first_4_beats.plot()  # Graph the R waves as Xs on top of the heartbeats plt.plot(peaks, ekg_first_4_beats[peaks], 'x') plt.title('First 4 R Waves of Patient 100\'s EKG')`

![None](https://miro.medium.com/v2/resize:fit:700/1*aYOS-xDi5oFvyLtVaXi9Hw.png)

#### Conclusion

Congratulations! You have started to analyze your first electrocardiogram.

Here we have loaded an EKG but only identified the R waves. There are several more waves (P, Q, S, and T waves) to identify and measure after this, which we cover in [the next article](https://medium.com/@protobioengineering/heart-analysis-with-python-part-2-labeling-ekgs-with-code-a381dfd031ba) in our EKG analysis series.

If you'd like to keep learning more about how EKGs work, keep reading or check out our list of [EKG analysis articles](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4).

### Further Reading

If you'd like to learn a little more about how EKGs work, keep reading below or check out our list of [EKG analysis articles](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4). Electrocardiograms and cardiology are complex topics that require an understanding from multiple angles in order to master. Hopefully, we can help you get the hang of them with our series here on Medium.

### How does the EKG machine get a signal from the heart?

EKG machines get their signal by listening in on the electricity that is produced by heartbeats. The heart is ([mostly](https://blog.transonic.com/cardiothoracic-surgery/the-heart-is-more-than-a-pump)) a pump made of muscle with some nerves that run down the middle to coordinate the pumping. As the nerves fire from top to bottom and the muscle alongside them contracts, we can eavesdrop on these changes in electricity with a [simple amplifier circuit](https://www.instructables.com/Make-Your-Own-Electrocardiogram-ECG/). The amplifier produces the characteristic QRS complex that we see.

![None](https://miro.medium.com/v2/resize:fit:700/1*Wu7hkxf7v5WlrZ9J_0UQXQ.jpeg)

Illustration of a person receiving an electrocardiogram (from the [NIH on Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Ekg_NIH.jpg))

The peaks going up and down are just the electricity flowing up and down the heart. Ninja Nerd's [EKG Basics video](https://www.youtube.com/watch?v=CNN30YHsJw0) explains this more in-depth.

The physical wires that get attached to a person during an EKG are placed such that the wires for the main lead ("[lead II](https://ecgwaves.com/topic/ekg-ecg-leads-electrodes-systems-limb-chest-precordial/#ECG_Leads_I_II_and_III_Willem_Einthovens_original_leads)") are placed in direct alignment with the middle (or "[septum](https://www.medicalnewstoday.com/articles/septum-heart)") of the heart. That way, when the heartbeat happens, the wire closest to the bottom of the heart "sees" the electric current coming directly at it.

### What does it mean to "predict" a heart attack?

At first glance, this might seem like a good time to throw the EKG into a machine learning algorithm and see which patients are having or might eventually have a heart attack, and then call it a day.

**However,** we would be missing out on [a century of cardiology research](https://www.pfizer.com/news/articles/flashback_the_first_ecg) by doing that. There are [100s of known and named arrhythmias](https://litfl.com/ecg-library/diagnosis/)**.**

As far as the "prediction" of heart attacks goes, we need to specify whether we're asking one of **two questions**:

1. Will this rhythm turn into a heart attack within a few **months**/years?
2. Will this rhythm turn into a heart attack within a few **minutes**?

We ask, because it **changes how the doctor treats the arrhythmia**. There are some rhythms that might raise a doctor's eyebrow and cause them to prescribe you medication. There are other rhythms that might cause your doctor to call you an ambulance ride to the emergency room.

![None](https://miro.medium.com/v2/resize:fit:700/0*PrCmPrS5EMVHJAvV)

An emergency room in Bayamón, Puerto Rico. Photo by [Luis Sánchez](https://unsplash.com/@gvbrio?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

### What do heart attacks look like?

**As a reminder, please DO NOT use this information to make medical decisions for yourself or others.** Please consult a licensed physician about any medical concerns, or visit your nearest emergency department, or call 911 or [your region's equivalent emergency number](https://travel.state.gov/content/dam/students-abroad/pdfs/911_ABROAD.pdf).

On an EKG, heart attacks can be identified by **how certain parts of the EKG change shape**.

#### STEMI

For example, below is one of the deadliest heart rhythms, called a "STEMI" (pronounced "stemmy"):

![None](https://miro.medium.com/v2/resize:fit:700/1*GAWJQg0mDcjQ8gaYt3k7eA.jpeg)

The shape of the EKG changed such that the **ST segment** (the line between the S wave and T wave) is **elevated**. This is caused by incompleteness of the ventricle contraction during the R wave due to a blockage or injury to cardiac muscle cells. ([Learn more on YouTube](https://www.youtube.com/watch?v=ond98UVBvyE).)

#### NSTEMI

An NSTEMI (pronounced "en-stemmy") is also a serious type of heart attack, but it does not show as an elevated ST segment on the EKG. Instead, the EKG might show ST depression, T wave inversion, or something similar.

![None](https://miro.medium.com/v2/resize:fit:700/1*x-ylKOeDAH7ng2Fk2Pu3Pw.png)

STEMI vs. NSTEMI on an electrocardiogram (from [McMaster University](https://wiki.mcmaster.ca/LIFESCI_4M03/group_1_presentation_3_-_parkinson_s_disease), Canada)

It is possible to have some ST elevation or depression and not be having a heart attack. It also possible to have no ST elevation and depression and still _be having_ a heart attack. Doctors will look at a patient's symptoms ("chest pain" or "shortness of breath") and correlate it with [blood tests](https://www.mountsinai.org/health-library/tests/troponin-test) to triangulate what is going on.

Note that, while STEMI and NSTEMI are the classic, big, bad heart attack rhythms, there is a new paradigm emerging in cardiology of [OMI vs. NOMI](https://litfl.com/omi-replacing-the-stemi-misnomer/). You'll hear about this more if you keep doing research and engineering projects in the cardiology/electrocardiography space.

### What else can an EKG tell us?

It's not just "heart attack" or "no heart attack." An EKG can even tell a doctor that:

- a patient's [electrolytes are off](https://ecgwaves.com/topic/ecg-electrolyte-imbalance-electrolyte-disorder-calcium-potassium-magnesium/)
- the tissue around the heart is [filled with fluid or swollen](https://www.ncbi.nlm.nih.gov/books/NBK534229/)
- the patient is using [cocaine or amphetamines](https://www.ahajournals.org/doi/full/10.1161/CIRCEP.121.010273)
- the patient [previously](https://www.healthline.com/health/heart-attack/how-far-back-can-an-ekg-detect-a-heart-attack) had a heart attack
- the patient has a [pacemaker](https://litfl.com/pacemaker-rhythms-normal-patterns/)

And more. These aren't definite diagnoses though. **An EKG can only indicate that something is likely** to be happening, but then a **doctor has to confirm it** with additional tests, like bloodwork, ultrasound, X-rays, and more.

> **So… a person's electrolytes are off. So what?**

Even something as simple as [imbalanced electrolytes](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3383164/) can cause multiple issues with the heart ([Levis, 2012](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3383164/)). First, our nervous system and heart muscles work based off of the electrolytes sodium, potassium, magnesium, calcium, and chloride. These ions are what allow the [electric impulses of the nervous system](https://en.wikipedia.org/wiki/Action_potential) to _**go**_ and cause the heart muscle to _**squeeze**_.

If there is an imbalance in these electrolytes, the heart might get the signal to beat more often than it should. Or it might get the signal too infrequently or not at all. Having the right balance of electrolytes is part of making sure that the timing of every part of this multi-chambered pump is just right.

> **Okay, so things are happening at the wrong time. How is this bad? The heart will still work, right?**

Kind of. If the pump is pumping too quickly, it won't have enough time to fill with blood, and each heartbeat will be just a [little too inadequate](https://www.sciencedirect.com/topics/veterinary-science-and-veterinary-medicine/tachycardia) to supply the body with blood and nutrients. If the [pump is pumping too slowly](https://www.cedars-sinai.org/health-library/diseases-and-conditions/b/bradycardia.html), then the body _still_ isn't getting enough blood, but for the opposite reason.

It's like pushing somebody on a swing. The timing has to be just right.

![None](https://miro.medium.com/v2/resize:fit:700/0*-sykpQJS6Gt50OrW)

Photo by [Kyle Johnson](https://unsplash.com/@kylejeffreys?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

### What about Fourier and spectral analysis?

The temptation may be to take a whole 5-minute EKG and visualize all of the frequencies at once to see what is going. However, doing this with a whole EKG means [you may miss some timing information](https://youtu.be/jnxqHcObNK4?si=KnaF5JouPNUqqe7L).

**Timing is everything in EKG analysis** ([with some exceptions](https://litfl.com/ecg-axis-interpretation/)). Though bargains always need to be made between [time and frequency](https://en.wikipedia.org/wiki/Uncertainty_principle#Signal_processing) in any [digital signal analysis](https://medium.com/@protobioengineering/list/digital-signal-processing-dsp-in-python-012629adec83), timing is the star of the show here.

Running a [Fourier transform](https://en.wikipedia.org/wiki/Fourier_transform) on an EKG does have some uses though, such as the ability to detect pacemakers, because these cause a sharp, distinct, downward inflection on the EKG. But for now, we will focus on labeling the PQRST waves by rote.

### What about machine learning?

Plugging an EKG into a time series machine learning algorithm may be helpful. However, plugging a spectrogram of the whole EKG into something like a visual transformer is misguided.

**It's not really "wrong," but it's wrong if it is the only thing that you do.** We are leaving [100 years of cardiology knowledge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6881865/) and [100+ well-known arrhythmias](https://litfl.com/ecg-library/diagnosis/) on the table if we cannot pick out PQRST waves and at least give them as features to a machine learning algorithm. By knowing about these waves, we can give our algorithm a leg up, and _then_ go looking for the rare things that humans missed.

If your friend tells you they threw 100 EKGs into a regression algorithm to find heart attacks but they can't tell you what a "QRS complex" is, please smack them (kindly) and then send them this article and [our whole series on EKGs](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4)!

### **Safety Reminder**

**DO NOT use any information from this article or any linked information to make medical decisions for yourself or others. This article was not written by a licensed physician.**

**If you have any medical concerns, please consult a licensed physician.** If you are concerned that you or another person are experiencing a medical emergency, please go to your nearest hospital's emergency department immediately or call 911 (or [your region's equivalent emergency number](https://travel.state.gov/content/dam/students-abroad/pdfs/911_ABROAD.pdf)). **Misuse of the information or code in this article can result in SERIOUS INJURY OR DEATH.**

### Next in This Series

1. [How the Heart Works](https://medium.com/@protobioengineering/how-to-analyze-the-heart-with-python-part-1-how-the-heart-works-efd800aa9ad0)
2. [How to Label EKGs with Code](https://medium.com/@protobioengineering/heart-analysis-with-python-part-2-labeling-ekgs-with-code-a381dfd031ba) (labeling P, Q, S, and T waves)
3. [How to Flatten a Wandering EKG](https://medium.com/@protobioengineering/heart-analysis-in-python-part-3-how-to-flatten-a-wandering-ekg-a58e01f8a89a)
4. [How to Calculate Heart Rate](https://medium.com/@protobioengineering/heart-analysis-with-python-part-4-calculating-heart-rate-12a651db5c47)
5. [How to Get Electocardiograms from the MIT-BIH Arrhythmia Database](https://medium.com/@protobioengineering/how-to-get-heart-data-from-the-mit-bih-arrhythmia-database-e452d4bf7215)

[All articles on EKG analysis in Python](https://medium.com/@protobioengineering/list/heart-and-electrocardiogram-analysis-in-python-9ed30d0083b4)

### More Resources

- [Life in the Fast Lane's ECG Library](https://litfl.com/ecg-library/)
- [Life in the Fast Lane's list of ECG arrhythmias A to Z](https://litfl.com/ecg-library/diagnosis/)
- [ECG 6-second guessing game](https://skillstat.com/tools/ecg-simulator/)

### Questions and Feedback

If you have questions or feedback, email us at protobioengineering@gmail.com or message us on [Instagram (@protobioengineering)](https://instagram.com/protobioengineering).

If you liked this article, consider supporting us by [donating a coffee](https://ko-fi.com/protobio/).

[#electrocardiogram](https://medium.com/tag/electrocardiogram "Electrocardiogram")[#python](https://medium.com/tag/python "Python")[#biomedical-engineering](https://medium.com/tag/biomedical-engineering "Biomedical Engineering")[#bioengineering](https://medium.com/tag/bioengineering "Bioengineering")[#digital-signal-processing](https://medium.com/tag/digital-signal-processing "Digital Signal Processing")