# Project Description UPDATED

Xyborg is an instrument based on one central design aspect, namely to be able to access sound manipulation via arm, hand and finger movement. It is a wearable arm-based interactive music system that allows the user to control a digital instrument through arm and hand motion. The instrument's design is derived from Michel Waisvisz's initial prototype of "The Hands" (see figure 1 below). Through a variety of motion-based sensor signals, the user is able to modulate the sound and play notes on a chromatic scale concurrently. 

By adding and rearranging the sensors, I intend to build upon Waisvisz's sophisticated design to produce an entertaining and enganging DMI.

## Introduction

Unleashing the potential musical expressiveness of arm hand and finger movement is certainly not new but still an increasingly exciting aspect of musical system design.  Instruments especially developed to be controlled with your upper extremities without being bound to a table reach back to the 1980s. Michel Waisvisz's instrument/ controller/ both "The Hands" are seen as a milestone in this field. Several other hand-based instruments/ controllers have been developed since then, some of them becoming commercial products like Imogen Heap's mi.mu gloves, while others stayed in the realm of being constantly developed further by the designer/ artist (Lady gloves). Separating likewise instruments into the category of being more a controller than an instrument is certainly not a "if this then that" question. It can be said, however, that most of the systems are more on the controller than instrument side, often in combination with singing voice manipulation. Xyborg is designed to function as a mobile gesture synthesizer and based on the first prototype of M.W. Hands. The motivation behind it was to find an engaging and exciting way to transform The Hands into a synthesizer while using sensors and techniques that had not been implemented in The Hands. 


## Related Works

Clearly, the main design inspiration has been M.W.'s instrument. 
## Design



The hands' frames will be constructed from wood. To counterbalance the weight of the hand portion, the frame extends along the lower arm. Two strap bands will secure the entire frame to the arm. The fingers must be bent in order to reach the touch/FSR sensors because they will not touch them when they are at rest. On each hand, the thumb will have access to push buttons with varying functions.

I plan to replace Waisvisz's original design, which called for 16 buttons on each hand, with six custom sensors (12 total, which correspond to 12 chromatic steps in an octave). These sensors are made of a self-built [force-sensitive resistorLinks to an external site.](http://iainmccurdy.org/diy/forcesensorfoam/forcesensorfoam.html) taped to a touch capacitor. By doing that, I hope to cover two aspects. Initially, by pressing and releasing the FSR, the user may control each note's attack and release, rather than just having note on/off functionality with the touch capacitor. Second, in order to be able to coordinate fingering while playing the "keyboard" blind, the self-made sensors provide a certain height and tactility. If the sensor lacked height and be flush with the plate it would be harder to hit the right note with the right finger.

Twelve sensors would be ideal for each hand, representing one octave on each hand; but, because to the Bela's constrained input capacity and the general selection of sensors, this is only possible with six sensors. Figure 2 shows how the sensors are arranged on each hand. Starting with an f-note on the left-hand little finger and finishing with an e-note on the right-hand little finger, the 12 notes in the chromatic scale are represented by 12 sensors. Since the middle and index fingers naturally have the greatest range and dexterity of all fingers, I put two notes on each of them.

The IMU and accelerometer will be fixed to the underside of the hand plates (IMU-left, accelerometer-right).

The synthesizer will be polyphonic and is based on additive and subtractive synthesis. A capacitive sensor strip must be touched to trigger an on/off note event.The user can change the note's envelope by pressing down on the sensor. Pressing down and releasing pressure will therefore be mapped to attack and release of the envelope.

The fusion pose of all axes of the IMU will be used to train a regression model (neuralnet pd-object) and mapped to the individual frequencies of a multiband filter. The trained model will then interpolate between data points and allow the user to manipulate the timbre of the sound in a rich and engaging way.

Using the accelerometer's linear acceleration data, a second neuralnet object will be trained to map the sensor data to multiple single-fold wavefolder objects. This will enable a rich-sounding distortion effect to be produced with the right hand.

Furthermore, velocity of the accelerometer will be calculated as the first order derivative of x-y-z acceleration and mapped to a small frequency range in order to be able to play with a vibrato effect.

The thumbs will have access to different functionalities through buttons: filter on/off, distortion on/off, vibrato on/off and octave up/down (2 buttons). The LED’s will signal whether modulation is on or off.

## Hardware

The whole system consists of

- 1 processing unit and circuitry housed inside a plastic casing which is strapped to the user’s waist, as well as a power bank 
    
- 2 wooden frames for the hands on which the sensors are mounted
        
- 2 accelerometers, 1 on each hand, fixed to the top of the frame
    
- 12 sensors (force-sensitive resistor + touch capacitor), 6 for each hand
    
- 6 SPST buttons for the thumbs as well as 3 RGB LED’s
    

All input pins will be used for the system:

- 2x Ic2P for the IMU and trill board respectively
    
- 3x AnaIN for accelerometer
    
- 9x DigIN (message rate) for push buttons and LED’s
    
- remaining 5 AnaIN and remaining 7 DigIN (audio rate) for the force-sensitive resistors
    

## Feasibility

The multiband filter, the wavefolder/distortion effect as well as 50% of the parts of the synthesizer have already been coded. The main focus of time will be on manufacturing the frame, the touch/FSR sensors and the training of the neural net objects. A sensitivity test has to be done with the FSR sensors in order to assure that long cable lines do not massively reduce sensitivity. If this should be the case I will opt out of the FSR sensors and only use the touch capacitors (and heightening them with cardboard). Reduced sensitivity because of cable length should not be a problem for the touch capacitors since they only provide note on/off information.

The instrument under consideration is a musical performance system that is entirely based on bela and the pure data coding environment, with no connection to a computer. It makes use of three different types of sensors which are all part of the the electronic kit.


## Evaluation



Please give the effects a rating in terms of playing overall controllability (includes control intimacy and reactiveness):  
- filter:  6
- vibrato/flanger:  5.67
- distortion: 5.67

A proper evaluation of a musical instrument takes time and it cannot be evaluated within a 20 minute session of letting people play with it. However, a short user study was conducted to 

Two viewpoints are interesting here. On the one hand, it is valuable to gain insight into how people perceive playing with the instrument, whether or not the ergonomics hinder playing and whether or not there are hidden affordances that could be build into the system. Since this instrument is preliminarily designed to fit the hand and arm dimensions of the author an evaluation with other people can only be so helpful. But the author gained valuable insights. These insights will be presented in the following paragraphs.


Three participants have been engaged in evaluating the system for half an hour each, all of which have been playing an instrument for more than a decade and feel very comfortable in playing an instrument that involves pressing keys or buttons (mean: 8.3).  Overall, the feedback I received was positive, with everyone who took part finding the instrument engaging and exciting to play. The evaluation consisted of two parts. First, participants were asked to execute several musical tasks, all increasing in difficulty and coordination. After that, they had to answer a short questionnaire in written form which consisted of ratings on a scale and questions concerning their experience during playing. This is a rather classical questionnaire style does not give a deep insight into the system, but rather helps to assess flaws and a general feeling with the instrument. 

Please give the musical tasks a rating in terms of being able to execute them (includes timing):

- single consecutive notes:  5
- intervals:  4.67
- arpeggios: 4.67
- chords:  5.67


The metaphor of a piano scale and keys was unclear, owing to the instrument's design, which prevents the thumb from playing. One participant attempted to use the thumb to play the pitch keys.

Everyone felt they could express musical ideas with the instrument, and the sensors triggered well and without noticeable latency (except for the thumb buttons).

Observing the participants while they played provided me with a lot of information on ergonomics (hand position, grabbing the frame, etc.) that I find very useful.

Before the concert, I'll focus on improving the controllability of the effects. Another quick fix is to replace the cheap buttons with more reliable ones.

### The Author's Reflection

Recapulating on the user study and the scores

Altough the average score on all musical tasks was above average, playing notes over a beat and being precise is still a big problem. The construction of the frame still limits the freedom of the hands. A large downside is that the thumb sits in a weird possible on top of 