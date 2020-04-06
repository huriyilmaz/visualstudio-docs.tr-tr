---
title: 'Test Alanı 8: Eklenti Anahtarlama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704388"
---
# <a name="test-area-8-plug-in-switching"></a>Test Alanı 8: Eklenti Değiştirme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE), geçerli kaynak denetimi eklentisini değiştirmek için kullanıcı arabirimine (UI) sahiptir. Bu test alanı, çözüm kaynağı denetimi için hangi eklentinin kullanılacağını seçme işlemi için test çalışmaları sağlar.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır.

- Geçerli kaynak kontrol eklentisi: **Araçlar** -> **Seçenekleri** -> **Kaynak Kontrolü** -> **Eklentisi Seçimi**.

- Kaynak denetimi bağlamadeğiştirin: **Dosya** -> **Kaynak Denetimi** -> **Değişikliği Kaynak Denetimi**...

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış
 Bir çözüm için kaynak kontrol eklentisini değiştirmek Visual Studio'dan çıkmadan veya çözümü yeniden yüklemeden mümkündür. Buna ek olarak, geçerli kaynak denetimi eklentisi, çözüm yüklendiğinde bir çözüm tarafından kullanılan fişe otomatik olarak dönüşür.

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıda, eklenti anahtarlama test alanı için özel test çalışmaları vereme leri yer almaktadır.

### <a name="case-8a-automatic-change"></a>Büyük/Küçük Harf 8a: Otomatik Değişim

#### <a name="expected-behavior"></a>Beklenen Davranış
 Bir kullanıcı kaynak denetimi altında olan bir çözüm yüklediğinde, çözüm otomatik olarak yüklenir ve uygun kaynak kontrol eklentisi akım olarak seçilir.

| Eylem | Test Adımları | Doğrulaması Beklenen Sonuçlar |
| - | - | - |
| Otomatik kaynak kontrol eklentisi değişikliği | 1. Geçerli olarak test altında eklenti seçin (**Araçlar** -> **Seçenekleri** -> **Kaynak Kontrol** -> **Eklentisi Seçimi**.)<br />2. Yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Başka bir eklenti seçin [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](örneğin, ).<br />5. Boşaltma çözüm istemini kabul edin.<br />6. Çözümü diskten yeniden açın. | Çözüm açıldı.<br /><br /> Test altında plug-in geçerli kaynak kontrol eklentisi. |

### <a name="case-8b-solution-based-change"></a>Örnek 8b: Çözüm tabanlı değişim

#### <a name="expected-behavior"></a>Beklenen Davranış
 Çözümün ilişkili kaynak denetim eklentisi değiştirilebilir.

| Eylem | Test Adımları | Doğrulaması Beklenen Sonuçlar |
|----------------------------------| - | - |
| Çözüm için eklenti değişikliği | 1. Geçerli olarak test altında eklenti seçin (**Araçlar** -> **Seçenekleri** -> **Kaynak Kontrol** -> **Eklentisi Seçimi**).<br />2. Yeni bir proje ve çözüm oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Çözüm kaynak denetiminden **(Kaynak Denetimini Değiştir** iletişim kutusunu kullanarak) silin.<br />5. Başka bir eklenti seçin [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](örneğin, ).<br />6. Boşaltılan solüsyonu diskten yeniden yükleyin.<br />7. Çözüm kaynağı denetimine ekleyin.<br />8. Çözüm kaynak denetiminden **(Kaynak Denetimi Değiştir** iletişim kutusunu kullanarak) silin.<br />9. Test altında eklentiyi tekrar seçin.<br />10. Boşaltılan solüsyonu diskten yeniden yükleyin.<br />11. Çözümü özgün konuma bağlayın **(Kaynak Denetimini Değiştir** iletişim kutusunu kullanarak). | Seçili eklenti kullanılarak kaynak denetimine çözüm eklenir. |

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
