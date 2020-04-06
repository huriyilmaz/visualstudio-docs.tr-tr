---
title: LPTEXTOUTPROC | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702799"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Kullanıcı tümleşik geliştirme ortamı (IDE) içinden bir kaynak denetim işlemi yürüttüğünde, kaynak denetim eklentisi işlemle ilgili hata veya durum iletileri iletmek isteyebilir. Eklenti bu amaçla kendi ileti kutularını görüntüleyebilir. Ancak, daha sorunsuz tümleştirme için eklenti dizeleri IDE'ye geçirebilir ve bu da dizeleri durum bilgilerini yerel olarak görüntüleyebilir. Bunun mekanizması işlev `LPTEXTOUTPROC` işaretçisidir. IDE hata ve durum görüntülemek için bu işlevi (aşağıda daha ayrıntılı olarak açıklanan) uygular.

IDE, `lpTextOutProc` [SccOpenProject'i](../extensibility/sccopenproject-function.md)ararken parametre olarak bu işleve bir işlev işaretçisi kaynak denetim eklentisine geçer. Bir SCC işlemi sırasında, örneğin, [sccGet'a](../extensibility/sccget-function.md) yapılan bir çağrının ortasında birçok dosya `LPTEXTOUTPROC` içeren, eklenti işlevi çağırabilir ve dizeleri düzenli olarak görüntülemek için geçirebilirsiniz. IDE bu dizeleri bir durum çubuğunda, bir çıkış penceresinde veya uygun şekilde ayrı bir ileti kutusunda görüntüleyebilir. İsteğe bağlı olarak, IDE belirli iletileri **İptal** düğmesiyle görüntüleyebilir. Bu, kullanıcının işlemi iptal etmesini sağlar ve IDE'ye bu bilgileri eklentiye geri aktarma olanağı sağlar.

## <a name="signature"></a>İmza
 IDE'nin çıkış işlevi aşağıdaki imzaya sahiptir:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parametreler

display_string

Görüntülenecek bir metin dizesi. Bu dize bir satır başı veya satır beslemesi ile sonlandırılmamalıdır.

mesg_type

İleti türü. Aşağıdaki tabloda bu parametre için desteklenen değerler listelenir.

|Değer|Açıklama|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|İleti Bilgi, Uyarı veya Hata olarak kabul edilir.|
|`SCC_MSG_STATUS`|İleti durumu gösterir ve durum çubuğunda görüntülenebilir.|
|`SCC_MSG_DOCANCEL`|İleti dizesi olmadan gönderildi.|
|`SCC_MSG_STARTCANCEL`|**İptal** düğmesini görüntülemeye başlar.|
|`SCC_MSG_STOPCANCEL`|**İptal** düğmesini görüntülemeyi durdurur.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|IDE'ye arka plan işleminin iptal edilip `SCC_MSG_RTN_CANCEL` edilmeyeceğini sorar: İşlem iptal edildiyse IDE döndürür; aksi takdirde, döner. `SCC_MSG_RTN_OK` Parametre, kaynak kontrol eklentisi tarafından sağlanan [Bir SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) yapısı olarak kullanılır. `display_string`|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Sürüm denetiminden alınmadan önce IDE'ye bir dosya hakkında bilgi vereb. `display_string` Parametre, kaynak kontrol eklentisi tarafından sağlanan bir [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) yapısı olarak kullanılır.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Sürüm denetiminden alındıktan sonra IDE'ye bir dosya hakkında bilgi vereb. `display_string` Parametre, kaynak kontrol eklentisi tarafından sağlanan bir [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) yapısı olarak kullanılır.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|IDE'ye bir arka plan işleminin geçerli durumunu bildirir. `display_string` Parametre, kaynak denetim eklentisi tarafından sağlanan bir [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) yapısı olarak kullanılır.|

## <a name="return-value"></a>Döndürülen değer

|Değer|Açıklama|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Dize görüntülendi veya işlem başarıyla tamamlandı.|
|SCC_MSG_RTN_CANCEL|Kullanıcı işlemi iptal etmek istiyor.|

## <a name="example"></a>Örnek
 IDE'nin Yirmi dosya adı olan [SccGet'ı](../extensibility/sccget-function.md) aradığını varsayalım. Kaynak denetim eklentisi bir dosyanın ortasında işlemi iptal önlemek istiyor olsun. Her dosyayı aldıktan `lpTextOutProc`sonra, her dosyadaki durum bilgilerini aktarAn ve rapor etme durumu yoksa bir `SCC_MSG_DOCANCEL` ileti gönderir. Eklenti herhangi bir zamanda `SCC_MSG_RTN_CANCEL` IDE'den iade değeri alırsa, başka dosya nın alınamasın diye alma işlemini hemen iptal eder.

## <a name="structures"></a>Yapılar

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsİptal

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Bu yapı `SCC_MSG_BACKGROUND_IS_CANCELLED` ileti ile gönderilir. İptal edilen arka plan işleminin kimliğini iletmek için kullanılır.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Bu yapı `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` ileti ile gönderilir. Alınacak dosyanın adını ve alma işlemini yapan arka plan işleminin kimliğini iletmek için kullanılır.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Bu yapı `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` ileti ile gönderilir. Belirtilen dosyayı alma sonucunu ve alma işlemini yapan arka plan işleminin kimliğini iletmek için kullanılır. Sonuç olarak verilebilecekler için [SccGet'ın](../extensibility/sccget-function.md) iade değerlerine bakın.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Bu yapı `SCC_MSG_BACKGROUND_ON_MESSAGE` ileti ile gönderilir. Bir arka plan işleminin geçerli durumunu iletmek için kullanılır. Durum, IDE tarafından görüntülenecek bir dize `bIsError` olarak ifade edilir ve`TRUE` iletinin önem derecesini gösterir (bir hata iletisi için; `FALSE` bir uyarı veya bilgilendirme iletisi için). Durumu gönderen arka plan işleminin kimliği de verilir.

## <a name="code-example"></a>Kod örneği
 Burada, arama nın `LPTEXTOUTPROC` yapısını nasıl göstererek iletiyi göndermek için arama nın kısa bir örneği verilmiştir. `SCC_MSG_BACKGROUND_ON_MESSAGE`

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
- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
