---
title: SccGetCommandOptions Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700829"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions fonksiyonu
Bu işlev, kullanıcıdan belirli bir komut için gelişmiş seçenekler ister.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 ıcommand

[içinde] Gelişmiş seçeneklerin istendiği komut (olası değerler için [Komut koduna](../extensibility/command-code-enumerator.md) bakın).

 ppvSeçenekleri

[içinde] Seçenek yapısı (aynı `NULL`zamanda olabilir).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_I_ADV_SUPPORT|Kaynak denetim eklentisi komut için gelişmiş seçenekleri destekler.|
|SCC_I_OPERATIONCANCELED|Kullanıcı kaynak denetimi eklentisinin **Seçenekler** iletişim kutusunu iptal etti.|
|SCC_E_OPTNOTSUPPORTED|Kaynak denetim eklentisi bu işlemi desteklemez.|
|SCC_E_ISCHECKEDOUT|Şu anda kullanıma kabul edilen bir dosyada bu işlemi gerçekleştiremez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetim eklentisinin `ppvOptions` = `NULL` belirtilen komutun gelişmiş seçenekler özelliğini destekleyip desteklemeyin belirlemek için bu işlevi ilk kez çağırır. Eklenti bu komut için özelliği destekliyorsa, kullanıcı gelişmiş seçenekler istediğinde (genellikle iletişim kutusunda **Gelişmiş** düğme olarak uygulanır) ve bu noktalar için `ppvOptions` null `NULL` olmayan bir işaretçi verdiğinde IDE bu işlevi yeniden çağırır. Eklenti, kullanıcı tarafından özel bir yapıda belirtilen gelişmiş seçenekleri depolar ve `ppvOptions`bu yapıya bir işaretçi döndürür. Bu yapı daha `SccGetCommandOptions` sonra, işlevin sonraki çağrıları da dahil olmak üzere, bu konuda bilinmesi gereken diğer tüm Kaynak Denetimi Eklentisi API işlevlerine geçirilir.

 Bir örnek bu durumu açıklığa kavuşturmak yardımcı olabilir.

 Bir kullanıcı **Get** komutunu seçer ve IDE bir **Al** iletişim kutusunu görüntüler. `SccGetCommandOptions` `SCC_COMMAND_GET` `ppvOptions` `NULL`IDE, ayarlı işlevi çağırır ve buna ayarlar. `iCommand` Bu, kaynak denetim eklentisi tarafından "Bu komut için gelişmiş bir seçeneğiniz var mı?" sorusu olarak yorumlanır. Eklenti dönerse, `SCC_I_ADV_SUPPORT`IDE **Get** iletişim kutusunda **Gelişmiş** bir düğme görüntüler.

 Kullanıcı **Gelişmiş** düğmesini ilk tıklatıldığında, IDE `SccGetCommandOptions` işlevi yeniden çağırır, bu`NULL``ppvOptions` kez bir `NULL` işaretçiye işaret etmeyen bir işlevle. Eklenti kendi **Seçenekleri Al** iletişim kutusunu görüntüler, kullanıcıdan bilgi ister, bu bilgileri kendi yapısına koyar ve `ppvOptions`'deki yapıya bir işaretçi döndürür.

 Kullanıcı aynı iletişim kutusunda **Gelişmiş'i** yeniden tıklatıyorsa, `SccGetCommandOptions` IDE `ppvOptions`işlevi değiştirmeden yeniden çağırır, böylece yapı eklentiye geri aktarılır. Bu, eklentinin iletişim kutusunu kullanıcının daha önce ayarladığının değerlerine yeniden başlatmasını sağlar. Eklenti, dönmeden önce yapıyı yerinde değiştirir.

 Son olarak, kullanıcı IDE'nin **Get** iletişim kutusunda **Tamam'ı** tıklattığında, IDE Gelişmiş seçenekleri içeren yapıyı geçerek `ppvOptions` [SccGet'ı](../extensibility/sccget-function.md)çağırır.

> [!NOTE]
> Komut, `SCC_COMMAND_OPTIONS` IDE, kullanıcının tümleştirmenin nasıl çalıştığını denetleyen tercihleri ayarlamasına olanak tanıyan bir **Seçenekler** iletişim kutusu görüntülediğinde kullanılır. Kaynak denetimi eklentisi kendi tercihleri iletişim kutusunu sağlamak istiyorsa, Bunu IDE'nin tercihleri iletişim kutusundagelişmiş **bir** düğmeden görüntüleyebilir. Eklenti, bu bilgilerin elde edilip kalıcı hale ilmesinden yalnızca sorumludur; IDE onu kullanmaz veya değiştirmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Komut kodu](../extensibility/command-code-enumerator.md)
