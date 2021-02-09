---
title: Hata kodları | Microsoft Docs
description: Bu makale, kaynak denetimi eklentisi API işlevlerine yönelik hata kodlarının, değerlerin ve açıklamaların bir listesini içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c9706f7c9cd5b25a3644af2f324fda01f448fa17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883408"
---
# <a name="error-codes"></a>Hata kodları
Bir kaynak denetimi eklentisi API işlevi bir hata döndürdüğünde, aşağıdaki hata kodlarından biri olması beklenir. Tüm hatalar negatif, uyarılar veya bilgilendirici hata kodları pozitif ve başarılı 0 ' dır.

|Hata Kodu|Değer|Açıklama|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Eklenti, iki adımda kaynak denetiminden dosya eklemeyi destekler. Daha fazla bilgi için bkz. [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Yerel dosya, kaynak denetim veritabanındaki dosyadan farklı (örneğin, [SccDiff](../extensibility/sccdiff-function.md) bu değeri döndürebilir).|
|`SCC_I_RELOADFILE`|5|Kaynak denetim işlemi sırasında yerel dosya değiştirildi; Mümkünse, IDE dosyayı yeniden yüklemeli.|
|`SCC_I_FILENOTAFFECTED`|4|Dosya etkilenmez.|
|`SCC_I_PROJECTCREATED`|3|Proje, kaynak denetim işlemi sırasında oluşturulmuştur (örneğin, flag belirtildiğinde bir [SccOpenProject](../extensibility/sccopenproject-function.md) çağrısı sırasında `SCC_OP_CREATEIFNEW` ).|
|`SCC_I_OPERATIONCANCELED`|2|İşlem iptal edildi.|
|`SCC_I_ADV_SUPPORT`|1|Eklenti, belirtilen komut için gelişmiş seçenekleri destekler. Daha fazla bilgi için bkz. [Sccgetcommandoseçenekler](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Başarılı.|
|`SCC_E_INITIALIZEFAILED`|-1|Hata: başlatma başarısız oldu.|
|`SCC_E_UNKNOWNPROJECT`|-2|Hata: proje bilinmiyor.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Hata: proje oluşturulamadı.|
|`SCC_E_NOTCHECKEDOUT`|-4|Hata: dosya kullanıma alınmamış.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Hata: dosya zaten kullanıma alındı.|
|`SCC_E_FILEISLOCKED`|-6|Hata: dosya kilitli.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Hata: dosya özel olarak kullanıma alındı.|
|`SCC_E_ACCESSFAILURE`|-8|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|`SCC_E_CHECKINCONFLICT`|-9|Hata: iade sırasında bir çakışma oluştu.|
|`SCC_E_FILEALREADYEXISTS`|-10|Hata: dosya zaten var.|
|`SCC_E_FILENOTCONTROLLED`|-11|Hata: dosya kaynak denetimi altında değil.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Hata: dosya kullanıma alındı.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Hata: belirtilen sürüm yok.|
|`SCC_E_OPNOTSUPPORTED`|-14|Hata: işlem desteklenmiyor.|
|`SCC_E_NONSPECIFICERROR`|-15|Özel olmayan hata.|
|`SCC_E_OPNOTPERFORMED`|-16|Hata, işlem gerçekleştirilmedi.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Hata: dosyanın türü, örneğin binary, kaynak kodu denetim sistemi tarafından desteklenmiyor.|
|`SCC_E_VERIFYMERGE`|-18|Dosya otomatik olarak birleştirildi ancak kullanıcı doğrulaması beklemede olduğundan denetlenmedi.|
|`SCC_E_FIXMERGE`|-19|Dosya otomatik olarak birleştirildi, ancak el ile çözümlenmesi gereken bir birleştirme çakışması nedeniyle iade edilmedi.|
|`SCC_E_SHELLFAILURE`|-20|Bir kabuk hatası nedeniyle hata oluştu.|
|`SCC_E_INVALIDUSER`|-21|Hata: Kullanıcı geçersiz.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Hata: proje zaten açık.|
|`SCC_E_PROJSYNTAXERR`|-23|Proje sözdizimi hatası.|
|`SCC_E_INVALIDFILEPATH`|-24|Hata: dosya yolu geçersiz.|
|`SCC_E_PROJNOTOPEN`|-25|Hata: proje açık değil.|
|`SCC_E_NOTAUTHORIZED`|-26|Hata: kullanıcının bu işlemi gerçekleştirme yetkisi yok.|
|`SCC_E_FILESYNTAXERR`|-27|Dosya sözdizimi hatası.|
|`SCC_E_FILENOTEXIST`|-28|Hata, yerel dosya yok.|
|`SCC_E_CONNECTIONFAILURE`|-29|Hata: bağlantı hatası oluştu.|
|`SCC_E_UNKNOWNERROR`|-30|Bilinmeyen hata.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Arka plan al işlemi şu anda devam ediyor.|

## <a name="macros-provided-for-quick-checking"></a>Hızlı denetim için girilen makrolar

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Açıklamalar
 Bağımsız değişken olarak geçirilen yerel dosyalar çalışma klasöründe yoksa, tüm kaynak denetimi eklentisi API işlevlerinin ( [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)ve [SccDiff](../extensibility/sccdiff-function.md)hariç) başarılı olması beklenir. Örneğin, IDE, çalışma klasöründe olmayan ancak kaynak denetim sisteminde bulunan bir dosya üzerinde [SccCheckout](../extensibility/scccheckout-function.md) veya [SccUncheckout](../extensibility/sccuncheckout-function.md) çağrısı verebilir. Bu çağrı başarılı olur. Yalnızca çalışma klasöründe veya kaynak denetimi sisteminde bir dosya olmadığında hata olması beklenen işlevdir.

 Ve gibi bazı işlevler, `SccAdd` `SccCheckin` `SCC_E_FILENOTEXIST` çalışma klasöründeki dosya mevcut olmadığında özel olarak döndürmelidir. Çalışma dosyası mevcut olmadığında, işlevler kaynak denetimi sisteminde geçerli bir dosya adı üzerinde çalışıyorsa, diğer işlevlerin başarılı olması beklenir.

 Eklenti, bir işlem sırasında dosyayı salt okunurdur olarak işaretlemiş olsa bile, kaynak denetimi eklentisinin çalışma klasöründeki bir dosyadaki ayrıcalıklarla ilgili varsayımsız olmaması gerekir. Çalışma klasöründeki bir dosya, eklenti denetiminin dışında taşınabilir, silinebilir ve değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
