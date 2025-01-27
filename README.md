Install the Langchain community module

```bash
npm i @langchain/community
```

Import the loaders

```javascript
import { PDFLoader } from '@langchain/community/document_loaders/fs/pdf'
import { YoutubeLoader } from '@langchain/community/document_loaders/web/youtube'
import { CharacterTextSplitter } from 'langchain/text_splitter'
```

Create the loaders using the community methods:

In `docsFromYTVideo`:

```javascript
const loader = YoutubeLoader.createFromUrl(video, {
  language: 'en',
  addVideoInfo: true,
})
const loadedDoc = await loader.load()
const splitter = new CharacterTextSplitter({
  separator: ' ',
  chunkSize: 2500,
  chunkOverlap: 200,
})
return await splitter.splitDocuments(loadedDoc)
```

In `docsFromPDF`:

```javascript
const docsFromPDF = async () => { const loader = new PDFLoader('./xbox.pdf')
  const loadedDoc = await loader.load()
  const splitter = new CharacterTextSplitter({
    separator: '. ',
    chunkSize: 2500,
    chunkOverlap: 200,
  })
  return await splitter.splitDocuments(loadedDoc)
```
