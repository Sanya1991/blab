# Blab

Blab is a tool for producing data according to slightly extended context
free grammars. You can think of it as a reverse grep, but with a more
descriptive language.



```
$ blab -e '97 10'
a
$ blab -e '(97 | 98)* 10'
baaaabbbbaaabababaaaababaaabbbababaaaabbbbbabbbbaabbbaaababbbbbb
$ blab -e '("foo" | "bar")* 10'
barfoofoo
$ blab -e '"(" "-"* ")" 10' -n 10
(-------------------------)
()
(-)
(-)
()
()
()
(-----------------------------)
(-------------------------)
(---)
$ blab -e 'output = S 10
           S = "foo" | "bar" | "(" S ")" | S " " S'
((bar bar foo))
$ blab -e 'output = S 10
           S = [1-9][0-9]* | "NaN" | "(" S ")" | S op S
           op = " " [+-*/] " "'
(((6) / 9) + 449428288325205608353298550945916151749155730959558272 * NaN)
$ blab -e '\("Beetlejuice"\)(", " \1){2} "!\n"'
Beetlejuice, Beetlejuice, Beetlejuice!
$ blab -e 'battle = hero " vs " hero " at " place "\n"
           hero = type person
           type = adjective | power | material | animal
           person = "wo"? "man" | "girl" | "boy" | "dog"
           animal = "bat" | "cat" | "spider"
           adjective = "super" | "duper" | "ultra" | "über"
           power = "laser" | "fire" | "electro" | "shrink" | "radar"
           material = "iron" | "steel" | "titanium"
           place = (verb | noun) noun "s"?
           verb = "shrink" | "topple" | "ditch" | "find" | "grow"
           noun = "wood" | "lake" | "mountain"'
überboy vs radarman at shrinkwoods
```

## Building

```
git clone https://github.com/aoh/blab
cd blab/
make
sudo make install 
blab --help
```

