## Acknowledgement

First and foremost, I would like to express my profound gratitude to God for giving me and everyone
who worked on this project the will, power, and knowledge to see this project through, for it was
truly and only by the grace, mercy, and blessing of God that this work came to light.

I would also like to extend my sincere thanks to everyone who worked on this project, for your
effort, support, and dedication were invaluable. I also would like to note that anything achieved
correctly was solely by the grace of God, and any shortcomings, errors, mistakes, and all otherwise
are entirely my own and on me to blame; may God forgive us for our mistakes.

---

# Adam

**A programming language with Rust's safety and Go's concurrency, written in any human tongue, that runs at the keystroke with nothing compiled and nothing interpreted.**

`v0.9.9` · no compiler, no interpreter · every tongue

**The site: [alobaid.github.io/adam-lang](https://alobaid.github.io/adam-lang/)**

Most languages keep a program as text in one human language, and rebuild everything from that text every time. Adam keeps a program as a list of **digests**. One digest is one thing the program does. It holds no word at all: a number that stands for the thing, and the machine's own instruction for it, already written, with gaps left for the values the program supplies.

Because the bytes are already inside the digests, the stored file is one fill away from running. A keystroke writes a value into a gap. There is no source file to parse, no tool to run, and nothing reading the program while it runs.

This repository is the Adam site: a single self-contained `index.html` that explains the idea with real bytes, real programs, and figures you can hover, tap, and pin.

## The idea in one figure

The smallest Adam program prints `Adam Lang` and stops. Stored, it is **110 bytes**: eight digests and nine bytes of the author's text. No words of any language are in it.

| part | size | what it is |
|---|---|---|
| where it sits | 1 byte | the digest's place in the program; the machine never sees it |
| which thing it is | 7 bytes | an identity drawn from the machine's random source, never reused |
| what the machine does | a few bytes | the instruction, with its gaps marked |

The same file, opened by three readers, looks like three different programs. It is one file, and none of them are copies.

```text
start                  开始                    開始
print "Adam Lang"      打印 "Adam Lang"        表示 "Adam Lang"
end                    结束                    終了
```

The text between the quotes is the author's and is never translated. Everything else is a view. Another reader opens the same file and sees the words they keep, and changing them costs the program nothing.

## The claim

Adam is three things, each with its reason on the line.

- **Every tongue.** Any human language, any words of any length, in any order. The stored file is digests, and what a reader sees is their own surface drawn from them.
- **Safety and concurrency.** Rust's safety and Go's concurrency, at the keystroke. Each digest's meaning was fixed once, when Rust's compiler and Go's agreed on it, so the properties belong to the digests before there is a program.
- **Speed.** At the keystroke, no build, it runs. Every digest was looked up and packed once, the day its word was proved. A program is a choice of digests, and each keystroke fills what a digest left open.

## The words are yours

Within one language nothing is fixed either. Three things belong to the reader.

**The flex.** A reader writes whatever they want to see, in their own hand. No table offers these words; they are one person's own writing, and the program is unchanged by them.

```text
the start of the program
write out "Adam Lang"
that is the end
```

**The order.** A digest carries its own place, so a surface may lay digests out however that reader reads best. A program that adds eight and three, written four ways, is the same three digests every time.

```text
add 8 and 3        add 8 to 3        8 and 3 add        8 + 3
```

**Both at once.** A line may simply be a sentence, and most of its words need not stand for anything.

```text
adding the two numbers 8 and 3 together
```

Three of those eight words are the program. The rest end at your screen. They are not stored, not carried anywhere, and not looked at when the program runs.

This matters because a fixed order and fixed word lengths are not neutral. They are one language's shape, and every reader of a differently shaped language pays for it: Arabic and Urdu run right to left, Japanese and Korean put the verb last, Russian moves words freely for emphasis, German makes one word where English wants four, and Chinese does the whole operation in one character between the values. Adam has no fixed shape, so none of them pay.

## How a word is proved

The digests are the one-way door. Programs are stored as them, so a wrong digest strands every file ever written. They are settled first, and not by drafting.

Every word is a **round**:

1. **The pick.** Which word, why this one now, and what needs it.
2. **Two forms.** The word is written twice, a few lines in Go and a few in Rust, each for this word alone.
3. **Both compiled and run** on the same input.
4. **Compared**, byte for byte. Nothing else enters: no specification, no opinion.
5. **Equal?** The digest is minted: where it sits, an identity drawn at random, the machine's bytes with their gaps.

Go's form goes in as that digest. That digest comes out as Rust's form. Two finished compilers say what the word means, and either they agree or they do not.

A round can end four ways: the outputs are equal and the digest is made; the outputs differ and the disagreement is recorded, never argued; the form uses something Adam refuses on purpose, such as a thread that starts itself or a hidden pointer, and the refusal is recorded with its reason; or nothing rules the word yet, and that is a finding for the list. Two things never happen: the language is never widened to make a word cross, and the list is never run in one go.

**The list** is one hundred and three words, chosen by one test: enough to write the software that sits closest to the machine. A driver, a tool, a script that moves bytes and prints. A vocabulary that carries that carries everyday programming with room to spare. The finished language is larger and comes later; nothing on the site waits on it.

After the list, Go's work is done. A program written from those words is stored as digests, patched to bytes, and runs. Neither Go nor Rust is in the picture any more.

## Every machine, every language

A digest's bytes are for one kind of machine. The bytes on the site are for the common desktop processor. There are two ways to run the same program elsewhere:

- **The patched run.** A table of bytes for the new machine, measured digest by digest and proved the way the words were, by comparison.
- **The Rust run.** The digests are written out as Rust and handed to `rustc`, which already targets every machine anyone runs. This needs no table, and it is the answer every new machine's table is checked against.

Any programming language can join. It writes its own forms of the words against the answers the rounds already hold, and brings its own parser. Its programs then get what Adam's get: stored as digests, patched to bytes, running with no compiler and no interpreter.

**Qalam** is the editor Adam is written in. It keeps the sheet of words each reader uses, and it fills a gap the moment a line is written.

## Repository layout

```text
adam-lang/
└── index.html   the whole site, built
```

The page is generated. Its head says so: the sources are `shell/` and `sections/`, and `ruby build.rb` writes this file. Those sources are not in this repository yet, so treat `index.html` as an artifact rather than something to edit by hand.

## Status

- **v0.9.9** of the site, one page and nine sections.
- The list stands at 103 words. The finished language is larger and comes later.
- The bytes on the site are x86-64. Other machines run through the Rust road today and get their own tables as they are measured.
- The measurements the speed figures rest on were taken on 2026-09-08 with Go 1.27.1 and rustc 1.97.1, and the public Benchmarks Game record read the same day.

## Credits

The site's face is [Lilex](https://github.com/mishamyrt/Lilex) (SIL OFL 1.1, Mikhail Panfilov), patched with [Nerd Fonts](https://www.nerdfonts.com/) glyphs (MIT, Ryan L McIntyre), with icons from [Lucide](https://lucide.dev/) (ISC, Lucide Contributors).

## License

Copyright (c) 2026 Talal Alobaid. All Rights Reserved. See [LICENSE](LICENSE). The embedded font and icons carry their own licenses, listed above.
