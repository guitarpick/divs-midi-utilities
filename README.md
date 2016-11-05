# divs-midi-utilities
Div's MIDI Utilities


<h2>The Utilities</h2>

<div class="entry">

<h3>alsamidi2pipe (Unix) and pipe2alsamidi (Unix)</h3>

<p>These utilities act as bridges between ALSA and the pipe-based utilities.</p>

<p>Usage: alsamidi2pipe [ --fifo &lt;fifo&gt;  ] [ --name &lt;client name&gt; ] [ --connect &lt;client name or number to which to connect&gt; &lt;port number&gt; ]</p>

<p>Usage: pipe2alsamidi [ --fifo &lt;fifo&gt;  ] [ --name &lt;client name&gt; ] [ --connect &lt;client name or number to which to connect&gt; &lt;port number&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>average-tempo (Windows, Unix), scale-tempo (Windows, Unix), offset-tempo (Windows, Unix), average-velocity (Windows, Unix), scale-velocity (Windows, Unix), and offset-velocity (Windows, Unix)</h3>

<p>These command line utilities can be used together for patching up multiple takes of a song to match one another.  The ability to analyze a specified section of a song is particularly useful if the tempo varies frequently, as is the case when the song has been through <em>tempo-map</em> or <em>metercaster</em>.</p>

<p>Usage: average-tempo [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] &lt;filename.mid&gt;</p>

<p>Usage: scale-tempo [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] --amount &lt;n&gt; [ --out &lt;filename.mid&gt; ] &lt;filename.mid&gt;</p>

<p>Usage: offset-tempo [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] --amount &lt;n&gt; [ --out &lt;filename.mid&gt; ] &lt;filename.mid&gt;</p>

<p>Usage: average-velocity [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] [ --track &lt;n&gt; ] &lt;filename.mid&gt;</p>

<p>Usage: scale-velocity [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] [ --track &lt;n&gt; ] --amount &lt;n&gt; [ --out &lt;filename.mid&gt; ] &lt;filename.mid&gt;</p>

<p>Usage: offset-velocity [ --tick | --beat | --mb | --mbt | --time | --hms | --hmsf ] [ --from &lt;time&gt; ] [ --to &lt;time&gt; ] [ --track &lt;n&gt; ] --amount &lt;n&gt; [ --out &lt;filename.mid&gt; ] &lt;filename.mid&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>beatbox (Windows)</h3>

<p>This command line utility is a very simple, percussion-oriented sampler.  It plays prerecorded audio files (WAV, AIFF, or AU) in response to MIDI note events.  This is most useful when combined with a pattern sequencer, but none is provided here at present.</p>

<p>Usage: beatbox [ --in &lt;n&gt; ] [ --voices &lt;n&gt; ] ( [ --config &lt;filename&gt; ] ) ...</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>brainstorm (Windows, Unix)</h3>

<p>This command line utility functions as a dictation machine for MIDI.  It listens for incoming MIDI events and saves them to a new MIDI file every time you pause in your playing for a few seconds.  The filenames are generated automatically based on the current time, so it requires no interaction.  I find it useful for recording brainstorming sessions, hence the name, and use it more than all the other utilities put together.</p>

<p>Usage (Windows version): brainstorm [ --in &lt;device id&gt; ] [ --timeout &lt;seconds&gt; ] [ --extra-time &lt;seconds&gt; ] [ --prefix &lt;filename prefix&gt; ] [ --verbose ]</p>

<p>Usage (original Unix version): brainstorm &lt;input fifo&gt; &lt;filename prefix&gt; &lt;timeout in seconds&gt;</p>

<p>Usage (ALSA-specific version): abrainstorm [ --prefix &lt;filename prefix&gt; ] [ --timeout &lt;seconds&gt; ] [ --confirmation &lt;command line&gt; ] [ --connect &lt;client name or number&gt; &lt;port number&gt; ]</p>

<p>Note that by default, the ALSA version does not connect up to an existing MIDI output port; rather it creates a new MIDI input port which you can then connect up as you see fit.  <em>aconnect</em>, <em>aconnectgui</em>, and <em>qjackctl</em> are common utilities which can be used to do this.</p>

<p>The confirmation option allows you to specify a command to execute whenever a file is saved, so that you know your music is safe.  I use it to play a short audio file, in keeping with brainstorm's "interfaceless" design, but you can get fairly elaborate if you want.  The filename will be substituted for each <code>%s</code> in the command.</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>fakesustain (Windows)</h3>

<p>This command line utility pre-applies sustain to note events.  It is useful for software-based synthesizers which have incomplete MIDI implementations that don't respond to real sustain messages.  (VST is a good idea, but can be frustrating in practice.)</p> 

<p>Usage: fakesustain [ --in &lt;n&gt; ] [ --out &lt;n&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>intervals (Unix)</h3>

<p>This filter-style utility plays parallel intervals for incoming MIDI messages.</p>

<p>Usage: intervals &lt;input_fifo&gt; &lt;output_fifo&gt; &lt;interval 1&gt; &lt;interval 2&gt; ...</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>joypedal (Windows) and joycc (Windows)</h3>

<p><em>Joypedal</em> is a command line/text mode interactive utility which requires custom hardware.  It looks for an organ style volume/expression pedal attached to the computer's joystick port, and translates its value into MIDI controller messages.  I wrote this because one of my old synthesizers hardwired its expression pedal to control volume, rather than making it assignable through MIDI.  Extremely simple instructions for building the joystick port adapter (for around 5 USD in parts) are included, but ATTEMPT THIS OR ANY OTHER CUSTOM HARDWARE PROJECT AT YOUR OWN RISK.</p>

<p><em>Joycc</em> is a command line utility which is functionally similar to <em>joypedal</em>, but is designed to work with real joysticks.  Up to three directional axes and four buttons on each of two joysticks can be mapped to separate MIDI controllers.</p>

<p>Usage: joypedal [ --out &lt;n&gt; ] [ --channel &lt;n&gt; ] [ --controller &lt;n&gt; ] [ --graph ]</p>

<p>Usage: joycc [ --out &lt;n&gt; ] [ --channel &lt;n&gt; ] [ --x1 &lt;n&gt; ] [ --y1 &lt;n&gt; ] [ --z1 &lt;n&gt; ] [ --a1 &lt;n&gt; ] [ --b1 &lt;n&gt; ] [ --c1 &lt;n&gt; ] [ --d1 &lt;n&gt; ] [ --x2 &lt;n&gt; ] [ --y2 &lt;n&gt; ] [ --z2 &lt;n&gt; ] [ --a2 &lt;n&gt; ] [ --b2 &lt;n&gt; ] [ --c2 &lt;n&gt; ] [ --d2 &lt;n&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>jumpoctave (Unix)</h3>

<p>This filter-style utility lets you use the pitch bend wheel as an octave jump control.</p>

<p>Usage: jumpoctave &lt;input fifo&gt; &lt;output fifo&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>lsmidiins (Windows) and lsmidiouts (Windows)</h3>

<p>These command line utilities display a numbered list of the Windows MIDI input and output ports.  Most of the other Windows utilities here refer to ports by number.</p>

<p>Usage: lsmidiins</p>

<p>Usage: lsmidiouts</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>metercaster (Windows, Unix) and tempo-map (Windows, Unix)</h3>

<p><em>Metercaster</em> is a command line utility which implements a brand new, unique algorithm for adjusting the timing of a MIDI sequence.  Unlike conventional quantization, meter casting does not replace the human characteristics of your playing with a mechanistic feel.  Instead, you place waypoints in the sequence to tell <em>metercaster</em> what the proper time should be for events of your choosing, and it interpolates among them, coming up with the proper times for the rest of the events.  This version is meant to be used iteratively, as you specify a single waypoint per invocation.  <em>Metercaster</em> is especially useful in conjunction with <em>brainstorm</em>, whose interfaceless design makes a metronome inappropriate.</p>

<p><em>Tempo-map</em> is a command line utility which can be used to acheive a similar effect to <em>metercaster</em>, but is far faster and more intuitive to use.  Inspired by, but more powerful than the "fit to improvisation" feature in Cakewalk, it expects the following usage model:  First, you record your performance without a metronome, as with <em>brainstorm</em>.  Next, ignoring any beat markers your sequencer might display, you add a click track consisting of one arbitrary note per beat, synchronized with your performance.  <em>Tempo-map</em> then processes the file, adjusting the timestamps of existing events and inserting new tempo events so that performance sounds the same when played back, but the notes will line up with beats when displayed in the sequencer.  You can then selectively delete the inserted tempo events, resulting in a steady but still completely nuanced recording.</p>

<p>Usage: metercaster [ --left ( marker &lt;name&gt; | cc &lt;number&gt; &lt;value&gt; ) ] [ --old-right ( marker &lt;name&gt; | cc &lt;number&gt; &lt;value&gt; ) ] [ --new-right ( marker &lt;name&gt; | cc &lt;number&gt; &lt;value&gt; ) ] [ --verbose ] &lt;filename&gt;</p>

<p>Usage: tempo-map --click-track &lt;n&gt; [ --out &lt;filename.mid&gt; ] &lt;filename.mid&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>midimon (Windows) and dispmidi (Unix)</h3>

<p>This command line utility pretty-prints incoming MIDI messages.  It can be useful for debugging complex MIDI setups, but there's nothing special about it.  The name differs by platform for historical reasons, but it works the same, regardless.</p>

<p>Usage (Windows version): midimon [ --in &lt;n&gt; ] ...</p>

<p>Usage (original Unix version): dispmidi &lt;input fifo&gt;</p>

<p>Usage (ALSA-specific version): adispmidi [ --connect &lt;client name or number&gt; &lt;port number&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>midithru (Windows)</h3>

<p>This command line utility reads from any number of Windows MIDI input ports, merges the streams together, and copies the result to any number of Windows MIDI output ports.  You can think of it as a combination of a hardware thru box and merge box.</p>

<p>Usage: midithru [ --in &lt;input device id&gt; ... ] [ --out &lt;output device id&gt; ... ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3><a href="../mish/">mish</a> (Windows, Unix)</h3>

<p>This command line utility is a compiler for a text-based music notation language which I invented, called "Mish" (<u>MI</u>DI <u>sh</u>orthand).  It converts Mish files into standard MIDI files.</p>

<p>Usage: mish --in &lt;input.mish&gt; --out &lt;output.mid&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>multiecho (Windows)</h3>

<p>This command line utility can add multiple echoes to your performance, with configurable delay, pitch offset, and velocity scaling.</p>

<p>Usage: multiecho [ --in &lt;n&gt; ] [ --out &lt;n&gt; ] [ --echo &lt;delay in ms&gt; &lt;note interval&gt; &lt;velocity percent&gt; ... ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>netmidic (Windows), pipe2net (Unix), alsamidi2net (Unix), netmidid (Windows), net2pipe (Unix), and net2alsamidi (Unix)</h3>

<p>These utilities all speak NetMIDI, a trivial network protocol I created which sends standard MIDI messages over a TCP/IP connection as fast as possible.  They can be used to connect up the MIDI systems on two different machines over a network connection, even if they are running different operating systems.  The clients forward messages from the local MIDI system to a NetMIDI server.  The servers forward messages sent by the clients to the local MIDI system.  Note that <em>pipe2net</em> and <em>net2pipe</em> are not actually MIDI specific, and are essentially the same thing as the standard <em>netcat</em> utility, but I didn't know that when I wrote them.</p>

<p>Usage (Windows version of the client): netmidic [ --in &lt;n&gt; ] [ --hostname &lt;name&gt; ] [ --port &lt;n&gt; ]</p>

<p>Usage (original Unix version of the client): pipe2net [ &lt;input fifo&gt; ] &lt;hostname&gt; &lt;port&gt;</p>

<p>Usage (ALSA-specific version of the client): alsamidi2net --server &lt;hostname&gt; &lt;port&gt; [ --name &lt;client name&gt; ] [ --connect &lt;client name or number to which to connect&gt; &lt;port number&gt; ]</p>

<p>Usage (Windows version of the server): netmidid [ --out &lt;n&gt; ] [ --port &lt;n&gt; ]</p>

<p>Usage (original Unix version of the server): net2pipe &lt;port&gt; [ &lt;output fifo&gt; ]</p>

<p>Usage (ALSA-specific version of the server): net2alsamidi --port &lt;port&gt; [ --name &lt;client name&gt; ] [ --connect &lt;client name or number to which to connect&gt; &lt;port number&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>normalizesmf (Windows, Unix) and verbosify (Unix)</h3>

<p><em>Normalizesmf</em> is a command line utility which provides a minimal demonstration of the <em>midifile</em> library.  It reads in a MIDI file, then writes it out again.  If your sequencer complains that a file is invalid, this normalizer might make it more palatable.</p>

<p><em>Verbosify</em> is a filter-style utility which normalizes incoming MIDI messages to a canonical form, like a realtime equivalent to <em>normalizesmf</em>.  It should not change the way things sound, but may make it easier to postprocess the stream.</p>

<p>Usage: normalizesmf &lt;filename&gt;</p>

<p>Usage: verbosify &lt;input fifo&gt; &lt;output fifo&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>notemap (Windows)</h3>

<p>This command line utility lets you remap the layout of notes on your MIDI keyboard.  I originally wrote it to see whether the guitar concept of "alternate tunings" could be applied to the piano.  That experiment was a failure, but notemap has since become essential to me for playing drums from the piano keyboard.</p>

<p>Usage: notemap &lt;filename&gt;.xml</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>onpedal (Windows) and onmessage (Windows)</h3>

<p><em>Onpedal</em> is a command line utility which runs a program or script every time you press the sustain pedal.  If you hold down the pedal for more time, it runs a second program.  I use it for turning pages in scanned copies of sheet music displayed on screen.  (If you have more than one pedal, you don't have to give up sustain.)</p>

<p><em>Onmessage</em> is similar, but it lets you assign different commands to different note and controller events.</p>

<p>Usage: onpedal --in &lt;n&gt; --command &lt;str&gt; [ --hold-length &lt;n&gt; ] [ --hold-command &lt;str&gt; ]</p>

<p>Usage: onmessage --in &lt;n&gt; ( --note-command &lt;number&gt; &lt;command&gt; | --note-down-command &lt;number&gt; &lt;command&gt; | --note-up-command &lt;number&gt; &lt;command&gt; | --controller-command &lt;number&gt; &lt;command&gt; | --controller-down-command &lt;number&gt; &lt;command&gt; | --controller-up-command &lt;number&gt; &lt;command&gt; | --program-command &lt;number&gt; &lt;command&gt; ) ...</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>padpedal (Windows)</h3>

<p>This command line utility is a variation on the idea of a sustenuto pedal (the middle pedal on most grand pianos) which adds a "pad" accompaniment to your playing.</p>

<p>Usage: padpedal [ --in &lt;port&gt; &lt;channel&gt; ] [ --pad-in &lt;port&gt; &lt;channel&gt; &lt;controller&gt; ] [ --out &lt;port&gt; &lt;channel&gt; ] [ --pad-out &lt;port&gt; &lt;channel&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>pedalnote (Windows)</h3>

<p>This command line utility plays a note whenever you press the sustain pedal.  I use it for kick drums.</p>

<p>Usage: pedalnote [ --in &lt;n&gt; ] [ --out &lt;n&gt; ] [ --channel &lt;n&gt; ] [ --note &lt;n&gt; ] [ --velocity &lt;n&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>playsmf (Windows)</h3>

<p>This command line utility is a generic MIDI file player.  Nothing special, but it gets along well with the other utilities.  Now based on the <em>midifile</em> library, this replaces the older <em>mciplaysmf</em>.</p>

<p>Usage: playsmf [ --out &lt;device id&gt; ] [ -- ] &lt;filename.mid&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>pulsar (Windows)</h3>

<p>This command line utility pulses any depressed notes according to a configurable rhythm.</p>

<p>Usage: pulsar [ --in &lt;n&gt; ] [ --out &lt;n&gt; ] [ --pulse &lt;time before pulse&gt; &lt;length of pulse&gt; &lt;time after pulse&gt; ] ...</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>qwertymidi (Windows), delta (Windows), and imp (Windows)</h3>

<p><em>Qwertymidi</em> is a command line/text mode interactive utility lets you use your computer keyboard as if it were a synthesizer keyboard.  It supports custom mapping of the keyboard layout by means of a config file.  A <a href="http://msdn.microsoft.com/en-us/library/aa299374%28v=VS.60%29.aspx">list of keyboard scan codes</a> will be useful for configuring the mapping.  Sample maps are included for the common piano-like tracker keyboard layout, the experimental von Janko piano keyboard layout from the 1850's, the Hayden concertina button layout, and a General MIDI drum kit.</p>

<p><em>Delta</em> is a fun to play, monophonic variation on <em>qwertymidi</em> which maps keys on the computer keyboard to relative intervals instead of absolute pitches.  It was inspired by the unusual <a href="http://www.samchillian.com/">Samchillian</a> MIDI controller I read about online.  It also supports custom keyboard mappings.</p>

<p><em>Imp</em> (<u>i</u>nput <u>m</u>apping <u>p</u>rogram) is a rudimentary but usable attempt to create a more powerful successor to <em>qwertymidi</em>.  It is implemented as a true GUI program in order to use newer Microsoft APIs which distinguish amongst multiple USB keyboards plugged into the same computer at the same time.</p>

<p>Usage: qwertymidi [ --out &lt;n&gt; ] [ --channel &lt;n&gt; ] [ --program &lt;n&gt; ] [ --velocity &lt;n&gt; ] [ --map &lt;str&gt; ]</p>

<p>Usage: delta [ --out &lt;n&gt; ] [ --channel &lt;n&gt; ] [ --program &lt;n&gt; ] [ --velocity &lt;n&gt; ] [ --map &lt;str&gt; ]</p>

<p>Usage: imp [ &lt;filename&gt; ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>rw (Unix)</h3>

<p>On some operating systems, devices such as <code>/dev/midi</code> can only be opened by a single program at a time, which is a problem if you want different programs to read and write to it simultaneously.  This utility, while not necessarily MIDI specific, can be used to split out a device's input and output to separate FIFOs.</p>

<p>Usage: rw &lt;device file&gt; &lt;input fifo&gt; &lt;output fifo&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>sendmidi (Windows)</h3>

<p>This command line utility sends a single specified MIDI message.  It can be used for scripting, or as a poor man's knob box.</p>

<p>Usage: sendmidi [ --out &lt;port&gt; ] ( --note-off &lt;channel&gt; &lt;pitch&gt; &lt;velocity&gt; | --note-on &lt;channel> &lt;pitch&gt; &lt;velocity&gt; | --key-pressure &lt;channel&gt; &lt;pitch&gt; &lt;amount&gt; | --control-change &lt;channel&gt; &lt;number&gt; &lt;value&gt; | --program-change &lt;channel&gt; &lt;number&gt; | --channel-pressure &lt;channel&gt; &lt;amount&gt; | --pitch-wheel &lt;channel&gt; &lt;amount&gt; )</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>smftoxml (Windows, Unix) and xmltosmf (Windows, Unix)</h3>

<p>These command line utilities convert a MIDI file into an ad hoc XML equivalent and back.  This can be useful for seeing exactly what is in the file, and how it is arranged in the data structures of the <em>midifile</em> library.  Using the two utilities together, you can modify MIDI files with a text editor or even with XSLT.</p>

<p>Usage: smftoxml &lt;filename&gt;</p>

<p>Usage: xmltosmf &lt;filename&gt;.xml &lt;filename&gt;.mid</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>transpose (Unix)</h3>

<p>This filter-style utility transposes incoming MIDI messages by a specified interval.</p>

<p>Usage: transpose &lt;input fifo&gt; &lt;output fifo&gt; &lt;interval&gt;</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>velocityfader (Windows)</h3>

<p>This command line utility scales incoming note velocities according to the current value of a specified continuous controller.  This gives you a different sort of volume control than normal, in that it only affects new notes coming in, leaving the sustained ones alone.  It can also be used to add pedal-operated volume control to a synth that doesn't support standard expression messages.</p>

<p>Usage: velocityfader [ --in &lt;n&gt; ] [ --out &lt;n&gt; ] [ --controller &lt;n&gt; ] [ --inverted ]</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>xmidiqwerty (Unix)</h3>

<p>This is an experimental, partially completed program which lets you use a MIDI keyboard as a chording text keyboard in X11.  It runs as a standard program sending synthetic keyboard events rather than an IME, so it does not require any complex installation nor disrupt the use of your normal keyboard.</p>

<p>Usage: xmidiqwerty (reads from standard input)</p>

</div><!-- class="entry" -->

<h2>Useful Libraries Also Provided</h2>

<div class="entry">

<h3>midifile (Windows, Unix)</h3>

<p>This powerful and practical library allows you to read and write Standard MIDI Files (SMF), and provides a data structure for MIDI sequences.  Essentially, it is the core of a MIDI sequencer without the user interface and the realtime recording and playback functionality.</p>

</div><!-- class="entry" -->
<div class="entry">

<h3>midimsg (Unix)</h3>

<p>This library provides an abstraction around raw realtime MIDI streams.  It hides annoying complexities like running status and active sensing.  Unnecessary for Windows or native ALSA programs, since this functionality is already provided for you there.</p>

</div><!-- class="entry" -->

<h2>Download</h2>

<p>These utilities are free and open source, provided under terms of the <a href="http://www.opensource.org/licenses/bsd-license.php">BSD license</a>.</p>

<p><a href="midi-utilities-20121006.zip">midi-utilities-20121006.zip</a> (1.5Mb)</p>

<p>Source is managed under the project <a href="https://github.com/dgslomin/divs-midi-utilities/">divs-midi-utilties</a> at Github's code hosting service.</p>

<h2>Related Links</h2>

<p>On Windows, a MIDI loopback utility is necessary to get the most out of these programs.  It will provide extra Windows MIDI ports which allow you to wire multiple MIDI programs together instead of speaking directly to your sound card or synthesizer.  While several such programs exist, both free and commercial, I am currently using Tobias Erichsen's free <a href="http://www.tobias-erichsen.de/">LoopMIDI</a>.</p>

<p class="small-print"><a href="../">home</a> &middot; dgslomin@alumni.princeton.edu &middot; last updated 2015.06.03</p>

