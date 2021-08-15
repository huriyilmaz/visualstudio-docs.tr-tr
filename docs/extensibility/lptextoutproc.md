---
title: LPTEXTOUTPROC | Microsoft Docs
description: LPTEXTOUTPROC işlev işaretçisi hakkında bilgi öğrenin. IDE Visual Studio hata ve durum görüntüleme işlevini uygulamaya alır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b266ea06ce79d0028e289210c7bfc11c62ea5ccde0f5050e246b38a4f06f5b16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321200"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Kullanıcı tümleşik geliştirme ortamının (IDE) içinden bir kaynak denetimi işlemi yürüttüğnde, kaynak denetimi eklentisi işlemle ilgili hata veya durum iletilerini iletmek istiyor olabilir. Eklenti, bu amaçla kendi ileti kutularını gösterebilirsiniz. Ancak, daha sorunsuz tümleştirme için eklenti, dizeleri IDE'ye iletir ve ardından bunları durum bilgilerini görüntülemenin yerel yolunda görüntüler. Bunun mekanizması işlev `LPTEXTOUTPROC` işaretçisidir. IDE, hata ve durum görüntülemeye ilişkin bu işlevi (aşağıda daha ayrıntılı olarak açıklanmıştır) uygulamaya alır.

IDE, `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md)çağrılırken parametresi olarak bu işleve bir işlev işaretçisi kaynak denetimi eklentisine geçer. Örneğin bir SCC işlemi sırasında, birçok dosya içeren [SccGet](../extensibility/sccget-function.md) çağrısının ortasında eklenti, görüntülemek için düzenli aralıklarla dizeler geçirme işlevini `LPTEXTOUTPROC` çağırabilirsiniz. IDE bu dizeleri bir durum çubuğunda, çıkış penceresinde veya uygun şekilde ayrı bir ileti kutusunda görüntüler. İsteğe bağlı olarak, IDE bir İptal düğmesiyle belirli iletileri  görüntüleyabiliyor olabilir. Bu, kullanıcının işlemi iptal etmelerini sağlar ve IDE'ye bu bilgileri eklentiye geri iletir.

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

Görüntü için bir metin dizesi. Bu dize satır başı veya satır besleme ile sonlandırılmamalı.

mesg_type

İletinin türü. Aşağıdaki tabloda bu parametre için desteklenen değerler listele devam eder.

|Değer|Açıklama|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|İleti Bilgi, Uyarı veya Hata olarak kabul edilir.|
|`SCC_MSG_STATUS`|İleti durumu gösterir ve durum çubuğunda görüntülenebilir.|
|`SCC_MSG_DOCANCEL`|İleti dizesiz gönderilir.|
|`SCC_MSG_STARTCANCEL`|İptal düğmesini **görüntülemeye** başlar.|
|`SCC_MSG_STOPCANCEL`|İptal düğmesini **görüntülemeyi** durdurur.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Arka plan işlemi iptal edilecekse IDE'ye sorar: İşlem iptal edildi ise IDE `SCC_MSG_RTN_CANCEL` döndürür; aksi takdirde `SCC_MSG_RTN_OK` döndürür. parametresi, kaynak denetim eklentisi tarafından `display_string` [sağlanan bir SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) yapısı olarak verilir.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|IDE'ye, sürüm denetiminden alınmadan önce bir dosya hakkında bilgi sağlar. parametresi, `display_string` kaynak denetim eklentisi tarafından sağlanan bir [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) yapısı olarak verilir.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|IDE'ye, sürüm denetiminden alındıktan sonra dosya hakkında bilgi sağlar. parametresi, `display_string` kaynak denetim eklentisi tarafından sağlanan bir [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) yapısı olarak verilir.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|IDE'ye bir arka plan işlemi için geçerli durumu söyler. parametresi, `display_string` kaynak denetim eklentisi tarafından sağlanan bir [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) yapısı olarak verilir.|

## <a name="return-value"></a>Döndürülen değer

|Değer|Açıklama|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Dize görüntülendi veya işlem başarıyla tamamlandı.|
|SCC_MSG_RTN_CANCEL|Kullanıcı işlemi iptal etmek istiyor.|

## <a name="example"></a>Örnek
 IDE'nin yirmi dosya adı [ile SccGet'i](../extensibility/sccget-function.md) çağır çağıran bir ad olduğunu varsayalım. Kaynak denetimi eklentisi, get dosyasının ortasında işlemi iptal etmek istiyor. Her dosyayı alan, çağırarak her dosyanın durum bilgilerini iletir ve rapor durumu `lpTextOutProc` `SCC_MSG_DOCANCEL` yoksa bir ileti gönderir. Eklenti herhangi bir zamanda IDE'den dönüş değeri alırsa, daha fazla dosya alınmayacak şekilde alma `SCC_MSG_RTN_CANCEL` işlemini hemen iptal eder.

## <a name="structures"></a>Yapılar

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Bu yapı iletiyle `SCC_MSG_BACKGROUND_IS_CANCELLED` birlikte gönderilir. İptal edilen arka plan işleminin kimliğini iletişim kurmak için kullanılır.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Bu yapı iletiyle `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` birlikte gönderilir. Alınması gereken dosyanın adını ve alma işlemi yapan arka plan işlemi kimliğini iletir.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Bu yapı iletiyle `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` birlikte gönderilir. Belirtilen dosyayı alma sonucundan ve alma işlemi yapılan arka plan işlemi kimliğine iletişim kurmak için kullanılır. Sonuç olarak nelerin ver [getiriLll](../extensibility/sccget-function.md) olduğunu görmek için SccGet için dönüş değerlerine bakın.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Bu yapı iletiyle `SCC_MSG_BACKGROUND_ON_MESSAGE` birlikte gönderilir. Bir arka plan işlemi geçerli durumunu iletişim kurmak için kullanılır. Durum, IDE tarafından görüntülenecek bir dize olarak ifade edildi ve iletinin önem derecesini gösterir ( bir hata iletisi için; uyarı için veya bilgilendirme `bIsError` `TRUE` iletisi `FALSE` için). Durumu gönderen arka plan işlemi kimliği de verilir.

## <a name="code-example"></a>Kod örneği
 Burada, iletiyi göndermek için çağrının yapısının nasıl atfı olduğunu `LPTEXTOUTPROC` gösteren kısa bir örnek ve ardından ve ardından bir çağrı `SCC_MSG_BACKGROUND_ON_MESSAGE` iletiyi gönderebilirsiniz.

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
