---
title: DisassemblyData | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737276"
---
# <a name="disassemblydata"></a>DisassemblyData
Tümleşik geliştirme ortamının (IDE) görüntülenmesi için bir sökme yönergesi açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi alanların doldurulduğuna işaret eden [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) sabiti.

`bstrAddress`\
Bazı başlangıç noktasından ofset olarak adres (genellikle ilişkili işlevin başlangıcı).

`bstrCodeBytes`\
Bu talimat için kod bayt.

`bstrOpcode`\
Bu talimatın opkodu.

`bstrOperands`\
Bu talimat için operands.

`bstrSymbol`\
Adresle ilişkili sembol adı (genel sembol, etiket vb.) ile ilişkilidir.

`uCodeLocationId`\
Bu sökülen satırın kod konum tanımlayıcısı. Bir satırın kod bağlam adresi diğerinin kod bağlamı adresinden büyükse, ilkinin sökülen kod konumu tanımlayıcısı da ikinci satırın kod konumu tanımlayıcıdan daha büyük olacaktır.

`posBeg`\
Sökme verilerinin başladığı belgedeki konuma karşılık gelen [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

`posEnd`\
Sökme verilerinin sona erdiği bir belgedeki konuma karşılık gelen [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

`bstrDocumentUrl`\
Dosya adı olarak temsil edilebilen metin `bstrDocumentUrl` belgeleri için alan, biçimi `file://file name`kullanılarak kaynağın bulunabileceği dosya adı ile doldurulur.

Dosya adı olarak gösterilemeyecek metin `bstrDocumentUrl` belgeleri için, belge için benzersiz bir tanımlayıcıdır ve hata ayıklama altyapısının [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) yöntemini uygulaması gerekir.

Bu alan, checksums hakkında ek bilgiler de içerebilir. Ayrıntılar için Açıklamalar'a bakın.

`dwByteOffset`\
Yönergedeki bayt sayısı kod satırının başından itibarendir.

`dwFlags`\
Hangi bayrakların etkin olduğunu belirten [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) sabiti.

## <a name="remarks"></a>Açıklamalar
Her `DisassemblyData` yapı bir sökme talimatı açıklar. Bu yapıların bir dizi [Oku](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yönteminden döndürülür.

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı yalnızca metin tabanlı belgeler için kullanılır. Bu yönerge için kaynak kod aralığı yalnızca bir deyim veya satırdan oluşturulan `dwByteOffset == 0`ilk yönerge için doldurulur, örneğin, .

Metin seli olmayan belgeler için, koddan bir belge bağlamı `bstrDocumentUrl` elde edilebilir ve alan boş bir değer olmalıdır. Alan `bstrDocumentUrl` önceki `bstrDocumentUrl` `DisassemblyData` dizi öğesindeki alanla aynıysa, null `bstrDocumentUrl` değeri ayarlayın.

Alan `dwFlags` `DF_DOCUMENT_CHECKSUM` bayrak kümesi varsa, ek checksum bilgileri `bstrDocumentUrl` alan tarafından işaret dize izler. Özellikle, null string sonlandırıcısonra, sırayla çekler bayt sayısını gösteren bir 4 bayt değeri takip ve sırayla checksum bayt tarafından takip checksum algoritması tanımlayan bir GUID izler. Bu alanın nasıl kodlanıp çözüleceklerine ilişkin bu [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]konudaki örneğe bakın.

## <a name="example"></a>Örnek
`DF_DOCUMENT_CHECKSUM` Bayrak ayarlanmışsa, `bstrDocumentUrl` alan dize dışında ek bilgiler içerebilir. Bu kodlanmış dize oluşturma ve okuma [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]işlemi basittir. Ancak, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]içinde , başka bir konudur. Merak edenler için, aşağıdaki örnek kodlanmış dize oluşturmak için [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] bir yol ve kodlanmış dize [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]çözmek için bir yol gösterir.

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
