```java
enum Instrument {
    Guitar,
    Piano
}

class ChordNote {
    Vec<Note> notes;
    Chord chord;
}

enum NoteLetter {
    A, B, C, D, E, F
}

class Note {
    int octave;
    int number;

    int getOctave();
    double getFrequency();
    NoteLetter getLetter();
}

enum ChordModifier {
    Major,
    Minor
}
enum SuspendedChord {
    Sus4,
    Sus7,
    Normal
}

class Chord {
    NoteLetter letter;
    boolean seven;
    ChordModifier modifier;
    SuspendedChord sus;
}

class Frequency {
    double freq;
}

interface MusicStream {
    Option<Chord> getCurrent();
    Vec<Frequency> getAll();
}

type MusicTimestamp = double;

class TimedNote {
    MusicTimestamp from;
    MusicTimestamp to;
    Frequency freq;
}

enum MusicStream {
    Microphone,
    Music
}
class Microphone {
    Option<Frequency> current();
    Vec<TimedNote> getAll();
}

class Music {
    Option<TimedNote> getNext();
    Vec<TimedNote> getAll();
    void resetTimestamp(MusicTimestamp)
}

class MusicRepresentationInput {
    Option<Music> music;
    Option<Microphone> microphone;
    boolean validatedCurrentNote;
    MusicTimestamp timestamp;
}

class Player {
    Music music;
    Microphone microphone;
    MusicTimestamp timestamp;

    MusicRepresentationInput getNext();
}

interface MusicRepresentation {
    draw(MusicRepresentationInput);
}
```
