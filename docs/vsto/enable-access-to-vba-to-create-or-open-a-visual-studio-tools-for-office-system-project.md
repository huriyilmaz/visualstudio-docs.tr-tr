---
title: VSTO projesini oluşturmak/açmak için VBA erişimi
titleSuffix: ''
description: Office için Visual Studio Araçları sistem projesi oluşturmadan veya açamadan önce Office VBA proje sistemine erişimi açıkça etkinleştirmeniz gerektiğini öğrenin.
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8c6e7d980301c0ad426c54e5f5838d64a11ca0bb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634097"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Microsoft Office sistem projesi için bir Visual Studio Araçları oluşturmak veya açmak için VBA'ya erişimi etkinleştirme

Microsoft Office sistem projesi için bir Visual Basic for Applications oluşturmadan veya açamadan önce Visual Basic for Applications Visual Studio Araçları (VBA) proje sistemine erişimi açıkça Microsoft Office gerekir.

 Microsoft Office geliştirme projeleri, Microsoft Office Word ve Microsoft Office Excel'daki Visual Basic for Applications (VBA) proje sistemine erişim gerektirir ancak Visual Basic for Applications. Hem Visual Basic hem de C# projelerinde denetimlerin tasarım zamanı desteği, Visual Basic for Applications bağlıdır.

 Makro Microsoft Office bazı virüsler, kendilerini yayma Visual Basic for Applications bir yol olarak proje sistemini otomatikleştirmeye çalışırken. Proje sistemine erişimi Visual Basic for Applications, makro virüslerin yayılmasını önlemeye yardımcı olan bir korumayı kaldırır. Ancak, normal makro güvenliği yerinde kalır, bu nedenle makro güvenlik düzeyi ve Office uygulamalarınız için bakımınız yapılan güvenilir yayımcılar listesi, bilgisayarınızda herhangi bir makronun çalıştırıp çalışmay olmadığını belirler.

> [!NOTE]
> Bu yalnızca geliştirme bilgisayarı için geçerlidir. Son kullanıcı bilgisayarlarında bu seçeneğin etkin olarak etkinleştirilmesi, Office gerekir.

 Visual Basic for Applications proje sistemine erişimin kendi başına devre dışı bırakılmasının sizi virüslerden korumaz, yalnızca bilgisayarınıza makro virüs bulaşırsa bazı virüslerin diğer belgelere yayılmasını durdurmanıza yardımcı olur. seçeneği, bilgisayarınız için eklenen bir koruma katmanı olarak varsayılan olarak devre dışıdır, ancak etkinleştirerek en iyi güvenlik uygulamalarını takip ediyorsanız bilgisayarınızı virüslere karşı daha duyarlı hale katmaz.

 Office makro virüslerine karşı en iyi koruma, Office veya Çok Yüksek güvenlik düzeyinde çalıştırarak yalnızca doğrulanmış, bilinen kaynaklardan gelen makrolara güvenmek ve güvenlik yamaları ve virüs tarayıcıları ile güncel kalmaktır.

 Erişime güven seçeneğini el ile **etkinleştirebilir veya Visual Basic Project ekleyebilirsiniz.**

 VBA veya COM hataları Office yüklemenizi onarabilirsiniz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Visual Basic projelerine erişimi etkinleştirmek veya devre dışı bırakmak için

1. Dosya **sekmesine** tıklayın.

2. **Seçenekler**’e tıklayın.

3. Güven **Merkezi'ne** ve ardından Güven **Merkezi'ne Ayarlar.**

4. Güven **Merkezi'nde** **Makrolar'a Ayarlar.**

5. Visual Basic Projelerine erişimi etkinleştirmek veya devre dışı **bırakmak için VBA** proje nesne modeline erişime güven'i işaretleyin veya Visual Basic kaldırın.

6. **Tamam**'a tıklayın.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>2007 Visual Basic sistemiyle Microsoft Office devre dışı bırakmak için

1. Word veya **Excel'daki** Araçlar menüsünde Makro'ya **gidin** ve Ardından Güvenlik'e **tıklayın.**

2. Güvenlik **iletişim** kutusunda Güvenilen Yayımcılar **sekmesine** tıklayın.

3. erişim erişimine güven ayarını etkinleştirmek veya devre dışı bırakmak **için temizlemeyi Visual Basic Project.**

4. **Tamam**'a tıklayın.

## <a name="to-set-your-office-macro-security-level"></a>Güvenlik düzeyinizi Office için

1. Dosya **sekmesine** tıklayın.

2. **Seçenekler**’e tıklayın.

3. Güven **Merkezi'ne** ve ardından Güven **Merkezi'ne Ayarlar.**

4. Güven **Merkezi'nde** **Makrolar'a Ayarlar.**

5. Makro **Ayarlar** bölümünde istediğiniz ayarı seçin.

6. **Tamam**'a tıklayın.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>2007 Office sistemiyle makro güvenlik düzeyinizi Microsoft Office için

1. Word veya **Excel'daki** Araçlar menüsünde Makro'ya **gidin** ve Ardından Güvenlik'e **tıklayın.**

2. Güvenlik **Düzeyi sekmesinde** istediğiniz ayarı seçin.

    Güvenlik **Düzeyi sekmesi** her düzeyle ilgili ayrıntıları içerir. Daha fazla bilgi için Yardım'da "Makro Güvenlik Düzeyleri" Office bakın.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>VBA'yı 2007 Microsoft Office yüklemek için

1. Bu Denetim Masası Program Ekle **veya Kaldır veya Programlar** ve **Özellikler'i çalıştırın.**

2. Şu Office programlar **listesinden Şu anda yüklü olan programlar'ı** seçin.

3. **Değiştir**’e tıklayın.

4. Özellik **Ekle veya Kaldır'ı seçin** ve ardından Devam'a **tıklayın.**

5. Uygulamaların **gelişmiş özelleştirmesi seçin'i seçin** ve ardından İleri'ye **tıklayın.**

6. Uygulamalar **Office araçlar için** güncelleştirme seçeneklerini seçin listesinde Paylaşılan **Özellikler'i genişletin.**

7. öğesinin yanındaki açılan menüyü **açın Visual Basic for Applications** Bilgisayarım'dan **Çalıştır'a tıklayın.**

8. **Devam**’a tıklayın.

9. **Kapat**’a tıklayın.

## <a name="to-repair-your-installation-of-office"></a>Yüklemenizi onarmak için Office

1. Bu Denetim Masası Program Ekle **veya Kaldır veya Programlar** ve **Özellikler'i çalıştırın.**

2. Yüklü programlar listesinden Office **sürümünü seçin.**

3. **Değiştir**’e tıklayın.

4. Yeniden **Yükle veya Onar'ı** seçin ve ardından Sonraki'ye **tıklayın.**

5. Yükleme **işlemimde Hataları algıla ve onar'Office yükle'ye** **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
