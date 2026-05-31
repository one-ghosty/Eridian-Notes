//Written by one_ghostyy

words = ["question","statement"];
notesSpecial = ["𝅘𝅥𝅰♫","𝅘𝅥𝅰𝅘𝅥𝅮"];

letters = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"];
notes = ["𝅘𝅥𝅘𝅥","𝅘𝅥𝅯𝅘𝅥𝅮","𝅗𝅥𝅘𝅥","𝅘𝅥𝅯♫","𝅘𝅥𝅗𝅥","𝅘𝅥𝅮𝅗𝅥","𝅘𝅥𝅮𝅘𝅥𝅮","𝅘𝅥𝅯𝅘𝅥","𝅘𝅥𝅘𝅥𝅮","♫𝅘𝅥𝅮","𝅗𝅥𝅗𝅥","𝅘𝅥𝅮𝅘𝅥𝅯","𝅗𝅥𝅘𝅥𝅮","𝅘𝅥𝅮𝅘𝅥","𝅘𝅥𝅘𝅥𝅯","𝅘𝅥𝅮♫","♫𝅗𝅥","𝅘𝅥𝅯𝅗𝅥","♫𝅘𝅥","𝅗𝅥♫","𝅘𝅥♫","𝅘𝅥𝅰𝅗𝅥","𝅗𝅥𝅘𝅥𝅯","𝅘𝅥𝅰𝅘𝅥𝅯","𝅘𝅥𝅘𝅥𝅰","𝅘𝅥𝅰𝅘𝅥"];

function forward(input){
	
	let str = input.trimEnd();
	
	for (let wordSpecial=0; wordSpecial < words.length; wordSpecial++) {
		let re = new RegExp(words[wordSpecial], "gi");
		str = str.replaceAll(re, notesSpecial[wordSpecial]);
	}
	
	for (let letter=0; letter < letters.length; letter++) {
		let re = new RegExp(letters[letter], "gi");
		str = str.replaceAll(re, notes[letter]);
	}
	
	return str;
};

function backward(input){

  let str = input.trimEnd();

  str = str.replaceAll(/\u{1D157}\u{1D165}/gu,String.fromCodePoint(0x1D15E));
  str = str.replaceAll(/\u{1D158}\u{1D165}/gu,String.fromCodePoint(0x1D15F));
  str = str.replaceAll(/\u{1D158}\u{1D165}\u{1D16E}|\u{1D15F}\u{1D16E}/gu,String.fromCodePoint(0x1D160));
  str = str.replaceAll(/\u{1D158}\u{1D165}\u{1D16F}|\u{1D15F}\u{1D16F}/gu,String.fromCodePoint(0x1D161));
  str = str.replaceAll(/\u{1D158}\u{1D165}\u{1D170}|\u{1D15F}\u{1D170}/gu,String.fromCodePoint(0x1D162));
  // fixes the weird messed up characters that twitter makes when you use them

  let strArray = str.split(/\s/);
  str = "";
  console.log(strArray);

  for (let word=0; word < strArray.length; word++){
    chars = strArray[word].match(/[♫𝅗𝅥𝅘𝅥𝅘𝅥𝅮𝅘𝅥𝅯𝅘𝅥𝅰][♫𝅗𝅥𝅘𝅥𝅘𝅥𝅮𝅘𝅥𝅯𝅘𝅥𝅰]?|[^♫𝅗𝅥𝅘𝅥𝅘𝅥𝅮𝅘𝅥𝅯𝅘𝅥𝅰]/gu);
    if ([...chars[chars.length-1]].length != 2 && !chars[chars.length-1].match(/[^♫𝅗𝅥𝅘𝅥𝅘𝅥𝅮𝅘𝅥𝅯𝅘𝅥𝅰]/)){
      console.log(chars);
      console.log(chars[chars.length-1]);
      return "ERROR: Malformed letters!";
    };

    for (let char = 0; char < chars.length; char++){
      if (!chars[char].match(/[^♫𝅗𝅥𝅘𝅥𝅘𝅥𝅮𝅘𝅥𝅯𝅘𝅥𝅰]/)){
        for (let noteSpecial=0; noteSpecial < notesSpecial.length; noteSpecial++) {
          let re = new RegExp(notesSpecial[noteSpecial], "gi");
          chars[char] = chars[char].replace(re, words[noteSpecial]);
        }

        for (let note=0; note < notes.length; note++) {
          let re = new RegExp(notes[note], "gi");
          chars[char] = chars[char].replace(re, letters[note]);
        }
      }
    };

    str = str + chars.join("") + " ";
  };

  str = str.trimEnd();
  str = str.toLowerCase();

  toCaps = str.matchAll(/(?<=[\?\.\!]\s)[a-z]|(?<!.)[a-z]/g);
  lowerArray = str.split("");

  for (const match of toCaps){
    lowerArray[match.index] = match[0].toUpperCase();
  }

  str = lowerArray.join("");

  return str;
};