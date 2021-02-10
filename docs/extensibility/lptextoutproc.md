---
title: LPTEXTOUTPROC | Microsoft Docs
description: LPTEXTOUTPROC işlev işaretçisi hakkında bilgi edinin. Visual Studio IDE, hata ve durumu görüntülemek için işlevi uygular.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef05b65b1a018772f4354062aa1be285c40b0d90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952180"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Kullanıcı, tümleşik geliştirme ortamının (IDE) içinden bir kaynak denetimi işlemi yürüttüğünde, kaynak denetimi eklentisi işlemle ilgili hata veya durum iletilerini iletmek isteyebilir. Eklenti, bu amaçla kendi ileti kutularını gösterebilir. Ancak, daha sorunsuz tümleştirme için, eklenti dizeleri IDE 'ye geçirebilir, bu da bunları durum bilgilerini görüntülemek için yerel bir şekilde görüntüler. Bunun mekanizması `LPTEXTOUTPROC` işlev işaretçisidir. IDE, hata ve durumu görüntülemek için bu işlevi uygular (aşağıda daha ayrıntılı olarak açıklanmıştır).

IDE, `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md)çağrılırken parametresi olarak bu işleve yönelik bir işlev işaretçisi olan kaynak denetimi eklentisine geçer. Bir SCC işlemi sırasında, örneğin, birçok dosya içeren [SccGet](../extensibility/sccget-function.md) öğesine yapılan çağrının ortasında eklenti, `LPTEXTOUTPROC` düzenli aralıklarla görüntülenecek dizeleri geçirerek işlevi çağırabilir. IDE, bu dizeleri bir durum çubuğunda, bir çıkış penceresinde veya ayrı bir ileti kutusunda uygun şekilde gösterebilir. İsteğe bağlı olarak, IDE belirli iletileri bir **iptal** düğmesi ile görüntüleyebiliyor olabilir. Bu, kullanıcının işlemi iptal etmesini sağlar ve IDE 'nin bu bilgileri eklentiye geri geçirebilmesini sağlar.

## <a name="signature"></a>İmza
 IDE 'nin çıkış işlevi aşağıdaki imzaya sahiptir:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametreler

display_string

Görüntülenecek metin dizesi. Bu dize bir satır başı veya bir satır akışı ile sonlandırılmamalıdır.

mesg_type

İleti türü. Aşağıdaki tabloda bu parametre için desteklenen değerler listelenmiştir.

|Değer|Açıklama|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|İleti bilgi, uyarı veya hata olarak kabul edilir.|
|`SCC_MSG_STATUS`|İleti durumu gösterir ve durum çubuğunda gösterilebilir.|
|`SCC_MSG_DOCANCEL`|İleti dizesi olmadan gönderilir.|
|`SCC_MSG_STARTCANCEL`|**İptal** düğmesini görüntülemeye başlar.|
|`SCC_MSG_STOPCANCEL`|**İptal** düğmesini görüntülemeyi durduruyor.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Arka plan işleminin iptal edilip edilmemeyi IDE ister: IDE `SCC_MSG_RTN_CANCEL` , işlem iptal edildiyse döndürür; Aksi takdirde, döndürür `SCC_MSG_RTN_OK` . `display_string`Parametresi, kaynak denetimi eklentisi tarafından sağlanan bir [Sccmsgdataısiptal](#LinkSccMsgDataIsCancelled) yapısı olarak dönüştürüldü.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Sürüm denetiminden alınmadan önce IDE 'ye bir dosya hakkında bilgi söyler. `display_string`Parametresi, kaynak denetimi eklentisi tarafından sağlanan bir [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) yapısı olarak dönüştürüldü.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Sürüm denetiminden alındıktan sonra IDE 'yi bir dosya hakkında söyler. `display_string`Parametresi, kaynak denetimi eklentisi tarafından sağlanan bir [Sccmsgdataonaftergetfile](#LinkSccMsgDataOnAfterGetFile) yapısı olarak dönüştürüldü.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Arka plan işleminin geçerli durumunun IDE 'sine söyler. `display_string`Parametresi, kaynak denetimi eklentisi tarafından sağlanan bir [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) yapısı olarak dönüştürüldü.|

## <a name="return-value"></a>Döndürülen değer

|Değer|Açıklama|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Dize görüntülendi veya işlem başarıyla tamamlandı.|
|SCC_MSG_RTN_CANCEL|Kullanıcı işlemi iptal etmek istiyor.|

## <a name="example"></a>Örnek
 IDE 'nin, yirmi dosya adı ile [SccGet](../extensibility/sccget-function.md) 'e çağrı sağladığını varsayalım. Kaynak denetimi eklentisi bir dosya al işleminin ortasında işlemin iptal edilmesini engellemek istiyor. Her bir dosyayı aldıktan sonra, `lpTextOutProc` her bir dosyaya durum bilgilerini çağırarak ve `SCC_MSG_DOCANCEL` rapor durumu yoksa bir ileti gönderir. Eklenti, IDE 'den dönüş değeri aldığında herhangi bir zamanda `SCC_MSG_RTN_CANCEL` , daha fazla dosya alınmaması için alma işlemini hemen iptal eder.

## <a name="structures"></a>Yapılar

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> Sccmsgdataısiptal edildi

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Bu yapı iletiyle birlikte gönderilir `SCC_MSG_BACKGROUND_IS_CANCELLED` . İptal edilen arka plan işleminin KIMLIĞINI iletmek için kullanılır.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Bu yapı iletiyle birlikte gönderilir `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` . Alınacak dosyanın adı ve alma işlemini yapan arka plan işleminin KIMLIĞI ile iletişim kurmak için kullanılır.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Bu yapı iletiyle birlikte gönderilir `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` . Belirtilen dosyanın alınması sonucunu ve alma işlemini yapan arka plan işleminin KIMLIĞINI iletmek için kullanılır. Sonuç olarak verilebilir olan [SccGet](../extensibility/sccget-function.md) için dönüş değerlerine bakın.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Bu yapı iletiyle birlikte gönderilir `SCC_MSG_BACKGROUND_ON_MESSAGE` . Arka plan işleminin geçerli durumunu iletmek için kullanılır. Durum, IDE tarafından görüntülenmek üzere bir dize olarak ifade edilir ve `bIsError` iletinin önem derecesini (bir `TRUE` hata iletisi için, `FALSE` bir uyarı veya bir bilgi iletisi için) gösterir. Durumu gönderen arka plan işleminin KIMLIĞI de verilir.

## <a name="code-example"></a>Kod örneği
 İşte `LPTEXTOUTPROC` `SCC_MSG_BACKGROUND_ON_MESSAGE` , çağrının yapısının nasıl alınacağını gösteren iletiyi göndermek için çağırmanın kısa bir örneği.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
