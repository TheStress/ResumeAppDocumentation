```plantuml
note "Not defined well yet" as ND

class Text <<DataStructure>> {
	string text;
	string font;
	float textSize;
	string style;
}

class TextDocument <<DataStructure>> {
	Text[] text;
}

class TextEditor {
	TextDocument currentDocument;
	TextDocument[] documentCopies;
}

object someTextEditorLibrary
```

