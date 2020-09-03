---
title: DisassemblyData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea21b4ae9e6e852efcc3625dc3af24478bd88155
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198818"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Görüntülenecek tümleşik geliştirme ortamı (IDE) için bir ayrıştırılmış tek derleme yönergesini açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 `dwFields`  
 Hangi alanların doldurulacağını belirten [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) sabiti.  
  
 `bstrAddress`  
 Bir başlangıç noktasından (genellikle ilişkili işlevin başlangıcı) bir konum olarak adres.  
  
 `bstrCodeBytes`  
 Bu yönergenin kod baytları.  
  
 `bstrOpcode`  
 Bu yönerge için opcode.  
  
 `bstrOperands`  
 Bu yönergenin işlenenleri.  
  
 `bstrSymbol`  
 Varsa, adres (genel simge, etiket, vb.) ile ilişkili simge adı.  
  
 `uCodeLocationId`  
 Bu ayrıştırılmış çizgi için kod konum tanımlayıcısı. Bir satırın kod bağlamı adresi diğerinin kod bağlamı adresinden büyükse, birincinin ayrıştırılmış kod konumu tanımlayıcısı ikincinin kod konumu tanımlayıcısından de daha büyük olur.  
  
 `posBeg`  
 Ayrıştırılmış verilerin başladığı bir belgedeki konuma karşılık gelen [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .  
  
 `posEnd`  
 Ayrıştırılmış verilerin bittiği bir belgedeki konuma karşılık gelen [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .  
  
 `bstrDocumentUrl`  
 Dosya adı olarak gösterilebilen metin belgeleri için, bu alan, `bstrDocumentUrl` biçimi kullanılarak kaynağın bulunabileceği dosya adıyla doldurulur `file://file name` .  
  
 Dosya adı olarak temsil edilemeyecek metin belgeleri için, `bstrDocumentUrl` belge için benzersiz bir tanımlayıcıdır ve hata ayıklama motorunun [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) yöntemini uygulaması gerekir.  
  
 Bu alan Ayrıca, sağlama toplamı hakkında ek bilgiler de içerebilir. Ayrıntılar için bkz. açıklamalar.  
  
 `dwByteOffset`  
 Yönergenin kod satırının başından itibaren olduğu bayt sayısı.  
  
 `dwFlags`  
 Hangi bayrakların etkin olduğunu belirten [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) sabiti.  
  
## <a name="remarks"></a>Açıklamalar  
 Her `DisassemblyData` Yapı, ayrıştırılmış bir tek derleme yönergesini açıklar. [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yönteminden bu yapıların bir dizisi döndürülür.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı yalnızca metin tabanlı belgeler için kullanılır. Bu yönergenin kaynak kodu aralığı yalnızca bir deyimden veya satırdan oluşturulan ilk yönerge için doldurulmuştur, örneğin, ne zaman `dwByteOffset == 0` .  
  
 Metinsel olmayan belgeler için, koddan bir belge bağlamı elde edilebilir ve `bstrDocumentUrl` alan null bir değer olmalıdır. Alan, `bstrDocumentUrl` `bstrDocumentUrl` önceki Array öğesindeki alanla aynı ise, öğesini `DisassemblyData` `bstrDocumentUrl` null bir değer olarak ayarlayın.  
  
 `dwFlags`Alan `DF_DOCUMENT_CHECKSUM` bayrak ayarlandıysa, ek sağlama bilgileri alanı tarafından işaret edilen dizeyi izler `bstrDocumentUrl` . Özellikle, null dize sonlandırıcısının ardından, sağlama toplamı algoritmasını tanımlayan bir GUID, ardından, sağlama toplamı içindeki bayt sayısını belirten 4 baytlık bir değer ve sırasıyla sağlama toplamı baytları tarafından izlenir. Bu alanın içindeki bu alanı kodlama ve kodunu çözme hakkında bu konudaki örneğe bakın [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] .  
  
## <a name="example"></a>Örnek  
 `bstrDocumentUrl`Bayrak ayarlandıysa, alan bir dize dışında ek bilgiler içerebilir `DF_DOCUMENT_CHECKSUM` . Bu kodlanmış dize oluşturma ve okuma işlemi açıktır [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] . Bununla birlikte, ' de, [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] başka bir önemi vardır. Merak eden kişiler için aşağıdaki örnek, ' [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] deki kodlanmış dizenin kodunun çözülmesi için bir yol ve bir yolu gösterir [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] .  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
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
            for (int i = 0; i < guidDataLength; i++)  
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
  
               // Parse string out.  String is assumed to be Unicode.  
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
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Okuyamaz](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
