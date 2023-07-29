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
TextDocument --> Text : uses 

class Document <<DataStructure>> {
	TextDocument mostRecentDocument;
	TextDocument[] documentCopies;
	
	OpenDocument();
}
Document --> TextDocument : uses

class ResumeMainPageDisplay {
	Document[] documents;
	
	UpdateDocuments(Document[] _documents);
	OpenDocument(Document document);
}

class TextEditor {
	TextDocument document;
	
	SetCurrentDocument(TextDocument _document);
	SetCurrentDocument(Document _document);
}
TextEditor --> TextDocument : uses
'TextEditor --> SomeDocumentEditorLibrary : uses


class CopySidePanelDisplay {
	TextDocument currentDocument;
	TextDocument[] documentCopies;
	
	MakeCopy();
}
CopySidePanelDisplay --> TextDocument : uses
CopySidePanelDisplay --> TextEditor : uses


class BlocksSidePanel {

}


```

