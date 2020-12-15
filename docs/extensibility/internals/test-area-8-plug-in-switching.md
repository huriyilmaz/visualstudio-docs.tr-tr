---
title: 'Test alanı 8: eklenti değiştirme | Microsoft Docs'
description: Bu kaynak denetimi test alanı, Visual Studio 'da çözüm kaynak denetimi için hangi eklentinin kullanılacağını seçme işlemi için test çalışmaları sağlar.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6c3a25aa9312073d3ce4a60752d41585fcee7b3
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487653"
---
# <a name="test-area-8-plug-in-switching"></a>Test Alanı 8: Eklenti Değiştirme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE), geçerli kaynak denetimi eklentisini değiştirmek için Kullanıcı arabirimine (UI) sahiptir. Bu test alanı, çözüm kaynak denetimi için hangi eklentinin kullanılacağını seçme işlemi için test çalışmaları sağlar.

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır.

- Geçerli kaynak denetimi eklentisi: **Araçlar**  ->  **Seçenekler**  ->  **kaynak denetimi**  ->  **eklentisi seçimi**.

- Kaynak denetimi bağlamasını Değiştir: **Dosya**  ->  **kaynağı denetimi**  ->  **kaynak denetimini Değiştir**...

## <a name="common-expected-behavior"></a>Yaygın beklenen davranış
 Bir çözüm için kaynak denetimi eklentisinin değiştirilmesi, Visual Studio 'dan çıkmadan veya çözümü yeniden yüklemeden mümkündür. Ayrıca, geçerli kaynak denetimi eklentisi, çözüm yüklendiğinde bir çözüm tarafından kullanılan bir otomatik olarak değişir.

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıdakiler, eklenti geçiş test alanı için özel test çalışmalardır.

### <a name="case-8a-automatic-change"></a>Case 8A: Otomatik değişiklik

#### <a name="expected-behavior"></a>Beklenen davranış
 Bir Kullanıcı kaynak denetimi altındaki bir çözümü yüklediğinde, çözüm otomatik olarak yüklenir ve uygun kaynak denetimi eklentisi geçerli olarak seçilidir.

| Eylem | Test adımları | Doğrulanacak beklenen sonuçlar |
| - | - | - |
| Otomatik kaynak denetimi eklentisi değişikliği | 1. geçerli test (**Araçlar**  ->  **Seçenekler**  ->  **kaynak denetimi**  ->  **eklentisi seçimi**) altındaki eklentiyi seçin.<br />2. yeni bir proje oluşturun.<br />3. çözümü kaynak denetimine ekleyin.<br />4. başka bir eklenti seçin (örneğin, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. kaldırma çözümü istemi 'ni kabul edin.<br />6. çözümü diskten yeniden açın. | Çözüm açıldı.<br /><br /> Test altındaki eklenti, geçerli kaynak denetimi eklentisidir. |

### <a name="case-8b-solution-based-change"></a>Durum 8B: çözüm tabanlı değişiklik

#### <a name="expected-behavior"></a>Beklenen davranış
 Çözümün ilişkili kaynak denetimi eklentisi değişmiş olabilir.

| Eylem | Test adımları | Doğrulanacak beklenen sonuçlar |
|----------------------------------| - | - |
| Bir çözüm için eklentinin değiştirilmesi | 1. geçerli test (**Araçlar**  ->  **Seçenekler**  ->  **kaynak denetimi**  ->  **eklentisi seçimi**) altındaki eklentiyi seçin.<br />2. yeni bir proje ve çözüm oluşturun.<br />3. çözümü kaynak denetimine ekleyin.<br />4. kaynak denetiminden çözümün bağlantısını kesin ( **kaynak denetimini Değiştir** iletişim kutusunu kullanarak).<br />5. başka bir eklenti seçin (örneğin, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. yüklü değilse çözümü diskten yeniden yükleyin.<br />7. çözümü kaynak denetimine ekleyin.<br />8. kaynak denetiminden çözümün bağlantısını kesin ( **kaynak denetimini Değiştir** iletişim kutusunu kullanarak).<br />9. test altındaki eklentiyi seçin.<br />10. kaldırılan çözümü diskten yeniden yükleyin.<br />11. çözümü özgün konuma bağlayın ( **kaynak denetimini Değiştir** iletişim kutusunu kullanarak). | Çözüm, kaynak denetimine seçili eklenti kullanılarak eklenir. |

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
