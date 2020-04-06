---
title: Hata Kodları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711835"
---
# <a name="error-codes"></a>Hata kodları
Kaynak Denetimi Eklentisi API işlevi bir hata döndürdüğünde, aşağıdaki hata kodlarından biri olması beklenir. Tüm hatalar negatif, uyarılar veya bilgilendirme hata kodları pozitif ve başarı 0'dır.

|Hata Kodu|Değer|Açıklama|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Eklenti, kaynak denetiminden dosya eklemeyi iki adımda destekler. Daha fazla bilgi için Bkz. [SccSetOption.](../extensibility/sccsetoption-function.md)|
|`SCC_I_FILEDIFFERS`|6|Yerel dosya kaynak denetim veritabanındaki dosyadan farklıdır (örneğin, [SccDiff](../extensibility/sccdiff-function.md) bu değeri döndürebilir).|
|`SCC_I_RELOADFILE`|5|Yerel dosya kaynak denetimi işlemi sırasında değiştirildi; IDE mümkünse dosyayı yeniden yüklemelidir.|
|`SCC_I_FILENOTAFFECTED`|4|Dosya etkilenmez.|
|`SCC_I_PROJECTCREATED`|3|Proje kaynak denetim işlemi sırasında oluşturuldu (örneğin, bayrak belirtildiğinde [SccOpenProject'e](../extensibility/sccopenproject-function.md) yapılan bir çağrı sırasında). `SCC_OP_CREATEIFNEW`|
|`SCC_I_OPERATIONCANCELED`|2|Operasyon iptal edildi.|
|`SCC_I_ADV_SUPPORT`|1|Eklenti, belirtilen komut için gelişmiş seçenekleri destekler. Daha fazla bilgi için Bkz. [SccGetCommandOptions.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_OK`|0|Başarılı.|
|`SCC_E_INITIALIZEFAILED`|-1|Hata: başlatma başarısız oldu.|
|`SCC_E_UNKNOWNPROJECT`|-2|Hata: proje bilinmiyor.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Hata: proje oluşturulamadı.|
|`SCC_E_NOTCHECKEDOUT`|-4|Hata: dosya kullanıma alınmadı.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Hata: dosya zaten kullanıma alındı.|
|`SCC_E_FILEISLOCKED`|-6|Hata: dosya kilitli.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Hata: dosya yalnızca kullanıma alındı.|
|`SCC_E_ACCESSFAILURE`|-8|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|`SCC_E_CHECKINCONFLICT`|-9|Hata: Iade sırasında bir çakışma oluştu.|
|`SCC_E_FILEALREADYEXISTS`|-10|Hata: dosya zaten var.|
|`SCC_E_FILENOTCONTROLLED`|-11|Hata: dosya kaynak denetimi altında değil.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Hata: dosya kullanıma alındı.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Hata: belirtilen bir sürüm yok.|
|`SCC_E_OPNOTSUPPORTED`|-14|Hata: işlem desteklenmiyor.|
|`SCC_E_NONSPECIFICERROR`|-15|Nonspecific hata.|
|`SCC_E_OPNOTPERFORMED`|-16|Hata, işlem gerçekleştirilmedi.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Hata: dosyanın türü, örneğin, ikili, kaynak kodu denetim sistemi tarafından desteklenmez.|
|`SCC_E_VERIFYMERGE`|-18|Dosya otomatik olarak birleştirilmiştir, ancak kullanıcı doğrulaması beklemede olduğu için denetlenmemiştir.|
|`SCC_E_FIXMERGE`|-19|Dosya otomatik olarak birleştirilmiştir, ancak el ile çözülmesi gereken bir birleştirme çakışması nedeniyle iade edilmemiştir.|
|`SCC_E_SHELLFAILURE`|-20|Kabuk arızası nedeniyle hata.|
|`SCC_E_INVALIDUSER`|-21|Hata: kullanıcı geçersizdir.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Hata: proje zaten açık.|
|`SCC_E_PROJSYNTAXERR`|-23|Proje sözdizimi hatası.|
|`SCC_E_INVALIDFILEPATH`|-24|Hata: dosya yolu geçersizdir.|
|`SCC_E_PROJNOTOPEN`|-25|Hata: proje açık değil.|
|`SCC_E_NOTAUTHORIZED`|-26|Hata: Kullanıcının bu işlemi gerçekleştirme yetkisi yoktur.|
|`SCC_E_FILESYNTAXERR`|-27|Sözdizimi hatası dosyala.|
|`SCC_E_FILENOTEXIST`|-28|Hata, yerel dosya yok.|
|`SCC_E_CONNECTIONFAILURE`|-29|Hata: bir bağlantı hatası oluştu.|
|`SCC_E_UNKNOWNERROR`|-30|Bilinmeyen hata.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Arka plan alma işlemi şu anda devam ediyor.|

## <a name="macros-provided-for-quick-checking"></a>Hızlı kontrol için sağlanan makrolar

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Açıklamalar
 Tüm Kaynak Denetimi Eklentisi API işlevleri [(SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)ve [SccDiff](../extensibility/sccdiff-function.md)hariç) bağımsız değişkenler çalışma klasöründe yoksa geçirilen yerel dosyalar başarılı olması beklenir. Örneğin, IDE çalışma klasöründe bulunmayan ancak kaynak denetim sisteminde bulunan bir dosyada [SccCheckout](../extensibility/scccheckout-function.md) veya [SccUncheckout'a](../extensibility/sccuncheckout-function.md) çağrı verebilir. Bu çağrı başarılı olur. Yalnızca çalışma klasöründe veya kaynak denetim sisteminde dosya olmadığında, başarısız olması beklenen işlevdir.

 Çalışma klasöründeki `SccAdd` `SccCheckin`dosya yoksa, `SCC_E_FILENOTEXIST` özellikle döndürme gibi belirli işlevler ve bu işlevler olmalıdır. İşlevler kaynak denetim sisteminde geçerli bir dosya adı üzerinde çalışıyorsa, çalışma dosyası yoksa diğer işlevlerin başarılı olması beklenir.

 Kaynak denetimi eklentisi, bazı işlem sırasında dosyayı salt okunur olarak işaretlemiş olsa bile, çalışma klasöründeki bir dosyadaki ayrıcalıklarla ilgili hiçbir varsayımda bulunmamalıdır. Çalışma klasöründeki bir dosya, eklentinin denetimi dışında taşınabilir, silinebilir ve değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
