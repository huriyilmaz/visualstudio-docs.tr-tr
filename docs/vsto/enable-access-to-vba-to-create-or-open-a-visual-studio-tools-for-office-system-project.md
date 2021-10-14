---
title: Bir sistem projesi oluşturmak/açmak için VBA VSTO
titleSuffix: ''
description: Office için Visual Studio Araçları sistem projesi oluşturamadan veya aç Office VBA proje sistemine erişimi açıkça etkinleştirmeniz gerektiğini öğrenin.
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
ms.openlocfilehash: e3cbda7b1bf0c4196bed030ee2935e696bc928f1
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972186"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Microsoft Office sistem projesi için bir Visual Studio Araçları oluşturmak veya açmak için VBA Microsoft Office etkinleştirme

Visual Basic for Applications sistem projesi için bir Visual Studio Araçları oluşturmadan veya açamadan önce Microsoft Office'daki Visual Studio Araçları (VBA) proje sistemine erişimi Microsoft Office gerekir.

 Microsoft Office geliştirme projeleri, Visual Basic for Applications Word ve Microsoft Office Microsoft Office Excel'da Visual Basic for Applications (VBA) proje sistemine erişim gerektirir Visual Basic for Applications. Hem Visual Basic hem de C# projelerinde denetimlerin tasarım zamanı desteği, Visual Basic for Applications bağlıdır.

 Makro Microsoft Office bazı virüsler, kendilerini yayma Visual Basic for Applications bir yol olarak proje sistemini otomatikleştirmeye çalışırken. Proje sistemine erişimi Visual Basic for Applications, makro virüslerin yayılmasını önlemeye yardımcı olan bir korumayı kaldırır. Ancak, normal makro güvenliği yerinde kalır, bu nedenle makro güvenlik düzeyi ve Office uygulamalarınız için bakımınız yapılan güvenilir yayımcılar listesi, bilgisayarınızda herhangi bir makronun çalıştırıp çalışmay olmadığını belirler.

> [!NOTE]
> Bu yalnızca geliştirme bilgisayarı için geçerlidir. Son kullanıcı bilgisayarlarında, çözümlerini çalıştırmak için bu seçeneğin etkinleştirilmesi Office gerekir.

 Visual Basic for Applications proje sistemine erişimin kendi başına devre dışı bırakılmasının sizi virüslerden korumaz, yalnızca bilgisayarınıza makro virüs bulaşırsa bazı virüslerin diğer belgelere yayılmasını durdurmanıza yardımcı olur. seçeneği, bilgisayarınız için eklenen bir koruma katmanı olarak varsayılan olarak devre dışıdır, ancak etkinleştirerek en iyi güvenlik uygulamalarını takip ediyorsanız bilgisayarınızı virüslere karşı daha duyarlı hale katmaz.

 Office makro virüslerine karşı en iyi koruma, Office'i Yüksek veya Çok Yüksek güvenlik düzeyinde çalıştırmak, yalnızca doğrulanmış, bilinen kaynaklardan gelen makrolara güvenmek ve güvenlik yamaları ve virüs tarayıcıları ile güncel kalmaktır.

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

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>2007 Visual Basic sistemiyle Microsoft Office etkinleştirmek veya devre dışı bırakmak için

1. Word veya **Excel'daki** Araçlar menüsünde Makro'ya **gidin** ve Ardından Güvenlik'e **tıklayın.**

2. Güvenlik **iletişim** kutusunda Güvenilen Yayımcılar **sekmesine** tıklayın.

3. erişim erişimine güven seçeneğini etkinleştirmek veya devre dışı bırakmak **için temizlemeyi Visual Basic Project.**

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

6. Uygulamalar **Office araçları için güncelleştirme** seçeneklerini seçin listesinde Paylaşılan **Özellikler'i genişletin.**

7. öğesinin yanındaki açılan menüyü açın **Visual Basic for Applications** Bilgisayarım'dan **Çalıştır'a tıklayın.**

8. **Devam**’a tıklayın.

9. **Kapat**’a tıklayın.

## <a name="to-repair-your-installation-of-office"></a>Yüklemenizi onarmak için Office

1. Bu Denetim Masası Program Ekle **veya Kaldır veya Programlar** ve **Özellikler'i çalıştırın.**

2. Yüklü programlar listesinden Office **sürümünü seçin.**

3. **Değiştir**’e tıklayın.

4. Yeniden **Yükle veya Onar'ı** seçin ve ardından Sonraki'ye **tıklayın.**

5. Yüklememde **hataları algıla ve onar'Office ve** yükle'ye **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
