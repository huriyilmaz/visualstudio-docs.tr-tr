---
title: 'Test Alanı 8: Eklenti Değiştirme | Microsoft Docs'
description: Bu kaynak denetimi test alanı, kaynakta çözüm kaynağı denetimi için hangi eklentinin kullanacağız seçkisi süreci için test Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: de08444c91ed0ab9bebc828873b7485ba97e6584
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158638"
---
# <a name="test-area-8-plug-in-switching"></a>Test Alanı 8: Eklenti Değiştirme
Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), geçerli kaynak denetimi eklentisini değiştirmek için kullanıcı arabirimine (UI) sahiptir. Bu test alanı, çözüm kaynağı denetimi için hangi eklentinin kullanacağız seçkisi için test işlemleri sağlar.

## <a name="command-menu-access"></a>Komut Menüsü Erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmalarında kullanılır.

- Geçerli kaynak denetimi eklentisi: **Araçlar**  ->  **Seçenekler Kaynak**  ->  **Denetimi** Eklentisi  ->  **Seçimi.**

- Kaynak denetimi bağlamayı değiştirme: **Dosya**  ->  **Kaynağı Denetimi Kaynak** Denetimi  ->  **Değiştir**...

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış
 Çözüm için kaynak denetimi eklentisini değiştirmek, çözümden çık Visual Studio yeniden yüklemeden mümkündür. Ayrıca, geçerli kaynak denetimi eklentisi çözüm yüklendiğinde bir çözüm tarafından kullanılan eklentiye otomatik olarak değişir.

## <a name="test-cases"></a>Test Çalışmaları
 Eklenti değiştirme test alanı için belirli test testleri aşağıda ve aşağıda ve listelemektedir.

### <a name="case-8a-automatic-change"></a>Durum 8a: Otomatik Değişiklik

#### <a name="expected-behavior"></a>Beklenen Davranış
 Kullanıcı kaynak denetimi altındaki bir çözümü yüklemişse çözüm otomatik olarak yüklenir ve uygun kaynak denetimi eklentisi geçerli olarak seçilir.

| Eylem | Test Adımları | Doğrulandı Beklenen Sonuçlar |
| - | - | - |
| Otomatik kaynak denetimi eklentisi değişikliği | 1. Testin altındaki eklentiyi geçerli olarak seçin (**Araçlar**  ->  **Seçenekler**  ->  **Kaynak Denetimi** Eklenti  ->  **Seçimi**.)<br />2. Yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Başka bir eklenti seçin (örneğin, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. Çözüm istemini kaldırmayı kabul et.<br />6. Çözümü diskten yeniden açın. | Çözüm açılır.<br /><br /> Test altındaki eklenti, geçerli kaynak denetimi eklentisidir. |

### <a name="case-8b-solution-based-change"></a>Durum 8b: Çözüm Tabanlı Değişiklik

#### <a name="expected-behavior"></a>Beklenen Davranış
 Çözümün ilişkili kaynak denetimi eklentisi değiştirilebilir.

| Eylem | Test Adımları | Doğrulandı Beklenen Sonuçlar |
|----------------------------------| - | - |
| Çözüm için eklenti değişikliği | 1. Test altındaki eklentiyi geçerli olarak seçin (**Araçlar**  ->  **Seçenekler**  ->  **Kaynak Denetimi** Eklenti  ->  **Seçimi**).<br />2. Yeni bir proje ve çözüm oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Çözümü kaynak denetiminden kaldırın (Kaynak Denetimi **Değiştir iletişim** kutusunu kullanarak).<br />5. Başka bir eklenti seçin (örneğin, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. Kaldırılmışsa çözümü diskten yeniden yükleyin.<br />7. Çözümü kaynak denetimine ekleyin.<br />8. Çözümü kaynak denetiminden kaldırın (Kaynak Denetimi **Değiştir iletişim** kutusunu kullanarak).<br />9. Testin altındaki eklentiyi yeniden seçin.<br />10. Kaldırılmışsa çözümü diskten yeniden yükleyin.<br />11. Çözümü özgün konuma bağlayın (Kaynak Denetimi **Değiştir iletişim** kutusunu kullanarak). | Çözüm, seçilen eklenti kullanılarak kaynak denetimine eklenir. |

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
