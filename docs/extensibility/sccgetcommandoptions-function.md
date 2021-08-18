---
description: Bu işlev, kullanıcıdan belirli bir komutun gelişmiş seçeneklerini ister.
title: Sccgetcommandocommanfunction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6b6fc42c15900b48826422d2474fb6a8048656ae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086358"
---
# <a name="sccgetcommandoptions-function"></a>Sccgetcommandoçenişlevi
Bu işlev, kullanıcıdan belirli bir komutun gelişmiş seçeneklerini ister.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 ICommand 'ı

'ndaki Gelişmiş seçeneklerin istendiği komut (olası değerler için [komut koduna](../extensibility/command-code-enumerator.md) bakın).

 Ppvdaoptions

'ndaki Seçenek yapısı (de olabilir `NULL` ).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_I_ADV_SUPPORT|Kaynak denetimi eklentisi, komut için gelişmiş seçenekleri destekler.|
|SCC_I_OPERATIONCANCELED|Kullanıcı, kaynak denetimi eklentisinin **Seçenekler** iletişim kutusunu iptal etti.|
|SCC_E_OPTNOTSUPPORTED|Kaynak denetimi eklentisi bu işlemi desteklemiyor.|
|SCC_E_ISCHECKEDOUT|Şu anda kullanıma alınmış bir dosya üzerinde bu işlem gerçekleştirilemez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 IDE, `ppvOptions` = `NULL` kaynak denetimi eklentisinin belirtilen komut için gelişmiş seçenekler özelliğini destekleyip desteklemediğini belirlemesi için bu işlevi ilk kez çağırır. Eklenti bu komut için özelliği destekliyorsa, Kullanıcı Gelişmiş seçenekleri istediğinde (genellikle iletişim kutusunda **Gelişmiş** bir düğme olarak uygulanır) ve `ppvOptions` bir IŞARETÇIYE işaret eden null olmayan bir işaretçi sağlayan bu işlevi yeniden çağırır `NULL` . Eklenti, Kullanıcı tarafından özel bir yapıda belirtilen tüm gelişmiş seçenekleri depolar ve içindeki bu yapıya bir işaretçi döndürür `ppvOptions` . Bu yapı daha sonra, işlevine sonraki çağrılar dahil olmak üzere bunun hakkında bilmeleri gereken tüm diğer kaynak denetimi eklenti API işlevlerine geçirilir `SccGetCommandOptions` .

 Örnek, bu durumun açıklanmasına yardımcı olabilir.

 Kullanıcı **Al** komutunu seçer ve IDE bir **Al** iletişim kutusu görüntüler. IDE, `SccGetCommandOptions` `iCommand` olarak ayarlanmış ve olarak ayarlanan işlevini `SCC_COMMAND_GET` çağırır `ppvOptions` `NULL` . Bu, "Bu komut için gelişmiş seçenekleriniz mı var?" sorusu olarak kaynak denetimi eklentisi tarafından yorumlanır. Eklenti döndürülürse `SCC_I_ADV_SUPPORT` , IDE **Get** iletişim kutusunda **Gelişmiş** bir düğme görüntüler.

 Kullanıcı **Gelişmiş** düğmesine ilk TıKLADıĞıNDA, IDE, `SccGetCommandOptions` Bu kez `NULL``ppvOptions` bir işaretçiye işaret eden, bu kez işlevi çağırır `NULL` . Eklenti kendi **Al seçenekleri** iletişim kutusunu görüntüler, kullanıcıdan bilgi ister, bu bilgileri kendi yapısına koyar ve içinde bu yapıya bir işaretçi döndürür `ppvOptions` .

 Kullanıcı aynı iletişim kutusunda **İleri** ' ye tıkladığında, `SccGetCommandOptions` `ppvOptions` Yapı EKLENTIYE geri geçirildiğinden, IDE işlevi değiştirmeden yeniden çağırır. Bu, eklentinin iletişim kutusunu kullanıcının daha önce ayarlamış olduğu değerlere yeniden başlatmasını sağlar. Eklenti, döndürmeden önce yapıyı yerinde değiştirir.

 Son olarak, Kullanıcı IDE 'nin **Al** Iletişim kutusunda **Tamam** ' a tıkladığında IDE, gelişmiş seçenekleri içeren ' de döndürülen yapıyı geçirerek [SccGet](../extensibility/sccget-function.md)' i çağırır `ppvOptions` .

> [!NOTE]
> Bu komut, `SCC_COMMAND_OPTIONS` IDE 'nin, kullanıcının tümleştirmenin nasıl çalıştığını denetleyen tercihleri ayarlamaya imkan tanıyan bir **Seçenekler** iletişim kutusu görüntülediğinde kullanılır. Kaynak denetimi eklentisi kendi tercihleri iletişim kutusunu sağlamak isterse, bunu IDE 'nin Tercihler iletişim kutusunda **Gelişmiş** bir düğmeden görüntüleyebilir. Eklenti, bu bilgileri almak ve kalıcı hale getirmekten yalnızca sorumludur; IDE bunu kullanmaz veya değiştirmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Komut kodu](../extensibility/command-code-enumerator.md)
