Source: [https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getmessage](<https://learn.microsoft.com/en-us/windows/win32/api/D3D11SDKLayers/nf-d3d11sdklayers-id3d11infoqueue-getmessage>)

# ID3D11InfoQueue::GetMessage


## -description

Get a message from the message queue.

## -parameters

### -param MessageIndex [in]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">UINT64</a></b>

Index into message queue after an optional retrieval filter has been applied. This can be between 0 and the number of messages in the message queue that pass through the retrieval filter (which can be obtained with <a href="/windows/desktop/api/d3d11sdklayers/nf-d3d11sdklayers-id3d11infoqueue-getnumstoredmessagesallowedbyretrievalfilter">ID3D11InfoQueue::GetNumStoredMessagesAllowedByRetrievalFilter</a>). 0 is the message at the front of the message queue.

### -param pMessage [out, optional]

Type: <b><a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_message">D3D11_MESSAGE</a>*</b>

Returned message (see <a href="/windows/desktop/api/d3d11sdklayers/ns-d3d11sdklayers-d3d11_message">D3D11_MESSAGE</a>).

### -param pMessageByteLength [in, out]

Type: <b><a href="/windows/desktop/WinProg/windows-data-types">SIZE_T</a>*</b>

Size of pMessage in bytes, including the size of the message string that the pMessage points to.

## -returns

Type: <b><a href="/windows/win32/com/structure-of-com-error-codes">HRESULT</a></b>

This method returns one of the following <a href="/windows/desktop/direct3d11/d3d11-graphics-reference-returnvalues">Direct3D 11 Return Codes</a>.

## -remarks

This method does not remove any messages from the message queue.

This method gets messages from the message queue after an optional retrieval filter has been applied.

Applications should call this method twice to retrieve a message - first to obtain the size of the message and second to get the message. Here is a typical example:


```

// Get the size of the message
SIZE_T messageLength = 0;
HRESULT hr = pInfoQueue->GetMessage(0, NULL, &messageLength);

// Allocate space and get the message
D3D11_MESSAGE * pMessage = (D3D11_MESSAGE*)malloc(messageLength);
hr = pInfoQueue->GetMessage(0, pMessage, &messageLength);

```


For an overview see <a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">Information Queue Overview</a>.

## -see-also

<a href="/windows/desktop/api/d3d11sdklayers/nn-d3d11sdklayers-id3d11infoqueue">ID3D11InfoQueue Interface</a>