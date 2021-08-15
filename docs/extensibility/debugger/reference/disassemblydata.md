---
description: Tümleşik geliştirme ortamının (IDE) görüntü için tek bir ayrı yönergeyi açıklar.
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e76a231891235f26ea4b4cd675f341376de4ff97ef7e6b2540a1cd1318504ce6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262561"
---
# <a name="disassemblydata"></a>DisassemblyData
Tümleşik geliştirme ortamının (IDE) görüntü için tek bir ayrı yönergeyi açıklar.

## <a name="syntax"></a>Syntax

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
Hangi [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) doldurulan sabiti.

`bstrAddress`\
Bir başlangıç noktasından uzaklık olarak adres (genellikle ilişkili işlevin başlangıcı).

`bstrCodeBytes`\
Bu yönerge için kod baytları.

`bstrOpcode`\
Bu yönerge için opcode.

`bstrOperands`\
Bu yönergenin işlenenleri.

`bstrSymbol`\
Varsa, adresle ilişkili sembol adı (ortak sembol, etiket vb.).

`uCodeLocationId`\
Bu ayrık satırın kod konumu tanımlayıcısı. Bir satırın kod bağlamı adresi başka bir satırın kod bağlamı adreslerinden büyükse, ilk satırın kod bağlamı tanımlayıcısı da ikinci satırın kod konumu tanımlayıcısından büyük olur.

`posBeg`\
TEXT_POSITION [](../../../extensibility/debugger/reference/text-position.md) verilerin başladığı belgedeki konuma karşılık gelen veri kaynağıdır.

`posEnd`\
Veri [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) verilerin sona erdiği belgedeki konuma karşılık gelen veri kaynağı.

`bstrDocumentUrl`\
Dosya adı olarak temsil edilen metin belgeleri için alanı, biçimi kullanılarak kaynağın buluna dosya `bstrDocumentUrl` adıyla `file://file name` doldurulur.

Dosya adı olarak temsil edil etmeyen metin belgeleri için, belge için benzersiz bir tanımlayıcıdır ve hata ayıklama altyapısı `bstrDocumentUrl` [GetDocument yöntemini uygulamalı.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Bu alan sağlamaları hakkında ek bilgiler de içerebilir. Ayrıntılar için bkz. Açıklamalar.

`dwByteOffset`\
Yönergenin bayt sayısı, kod çizgisinin başından itibarendir.

`dwFlags`\
Hangi [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) etkin olduğunu belirten bir sabittir.

## <a name="remarks"></a>Açıklamalar
Her `DisassemblyData` yapı, bir ayrım yönergesi açıklar. Bu yapıların dizisi [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yönteminden döndürülür.

TEXT_POSITION [](../../../extensibility/debugger/reference/text-position.md) yapısı yalnızca metin tabanlı belgeler için kullanılır. Bu yönergenin kaynak kod aralığı yalnızca bir deyiminden veya satırdan oluşturulan ilk yönerge için (örneğin, olduğunda) `dwByteOffset == 0` doldurulur.

Metinsel olmayan belgeler için, koddan belge bağlamı elde edilir ve `bstrDocumentUrl` alan null değer olmalıdır. Alan, `bstrDocumentUrl` önceki dizi `bstrDocumentUrl` öğesinde yer alanla `DisassemblyData` aynı ise değerini null `bstrDocumentUrl` değere ayarlayın.

Alanda `dwFlags` bayrağı `DF_DOCUMENT_CHECKSUM` ayarlanmışsa, ek sağlama kümesi bilgileri alanı tarafından işaret eden dizeyi `bstrDocumentUrl` izler. Özellikle, null dize sonlandırıcıdan sonra, sırasıyla sağlama toplam algoritmasını tanımlayan bir GUID izler ve ardından sağlama toplam değerindeki bayt sayısını belirten 4 bayt değeri gelir ve bu değerin ardından sağlama toplam baytları gelir. bu alanı içinde kodlama ve kodunu çözme hakkında bu konudaki Örnek'e [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] bakın.

## <a name="example"></a>Örnek
Bayrağın `bstrDocumentUrl` ayarlanmış olduğu alan, dize dışında ek `DF_DOCUMENT_CHECKSUM` bilgiler içerebilir. Bu kodlanmış dizeyi oluşturma ve okuma işlemi içinde [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] basittir. Ancak, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] içinde başka bir konudur. Merak edenler için aşağıdaki örnekte, kodlanmış dizeyi oluşturmanın bir yolu ve içinde kodlanmış dizenin kodunu [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] çözmenin bir yolu yer [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] alır.

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
