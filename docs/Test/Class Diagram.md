```plantuml
'note "Not defined well yet" as ND

class Text <<DataStructure>> {
	string text;
	string font;
	float textSize;
	string style;
}

class TextDocument <<DataStructure>> {
	Text[] text;
	string copyDate;
}
TextDocument ..> Text : uses 

class Document {
	TextDocument mostRecentDocument;
	TextDocument[] documentCopies;
	
	OpenDocument();
}
Document ..> TextDocument : uses

'class ResumeMainPageDisplay {
''	Document[] documents;
''	
''	UpdateDocuments(Document[] _documents);
''	OpenDocument(Document document);
''}

class TextEditor {
	Document document;
	Observer[] observers; // Using the observer design pattern


	SetCurrentDocument(Document _document);
	NotifyOnUpdate(); // this should notify any observers about updates to doucment
	OpenDocument(Document document);
}
TextEditor ..> Document : uses

class TextEditorDisplay {
	Document document;

	NotifyOnUpdate(); // Observing TextEditor, updates display
}
TextEditorDisplay --> TextEditor : uses

class CopySidePanelDisplay {
	Document document;	

	MakeCopy();
	NotifyOnUpdate(); // Observing TextEditor, updates display
	SetTextEditorDocument(TextDocument textDocument);
}
CopySidePanelDisplay --> TextEditor : uses


'class BlocksSidePanel {
'	Text[] blocks;
'}


```
![](https://www.plantuml.com/plantuml/png/ZPHDRzim38RF2P3_GFII55ZR-rBai6R7DaMpdeQXK6mc4QfAXaXjyuRzz-d3bXtN6GO4WJvUaOzUKfvDvzemmiM3OIXnBpMMy0ELWXhv0WJ1mtesdKqB9OZW2_vakBrT2nPRjgvWPt6rWj-pwOJOIdq0zefbDzqR7QTxPGJ7pQtyXJq1SQt2_CzfahKft1lgSyc2vEktORB2LBLND-5EmbnVhnByHt2415ssB6dZveKtG_o4XH-sIyk1n2EKpV3EL18f2FnlKw5kDOlBXFCE9Iyaf40qJqXFI7xdNaZzA0wubbGfKGU--NmoaZfazJlnxxaglG6jY1Oz-KlMNwO39vIPfbKbqQ0idql9naQhtXq8Tz_i2Ertj3wTQOQqX9iRUARO74VCwxxPI1uqL88PhGvvV80jyfspjkTvH_RIHvluVfNxUgFJZRtB8GqV9G4TZLCbw2W0eUkE1SJEE0ONpn2myVIk2367LHlre-cgneLGo94Y3jtgrM_Kj7DtILu6sxfO7p9wcQ8EcDfSLrUhVhs6SBvPwwqiyL5eLF_ccqJ0U_6AuT3YlFN_YHigtEDjxJvv4DoRDBQF4f-zPNv9dvGfNYaVZ6-e_NZiubxeyjZaVm40)