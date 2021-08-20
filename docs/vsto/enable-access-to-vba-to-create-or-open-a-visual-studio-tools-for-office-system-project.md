---
title: VSTO sistem projesi oluşturmak/açmak için VBA erişimi
titleSuffix: ''
description: Office için Visual Studio Araçları bir sistem projesi oluşturmadan veya açmadan önce Office VBA proje sistemine erişimi açıkça etkinleştirmeniz gerektiğini öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106386"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Microsoft Office sistemi projesi için Visual Studio Araçları oluşturmak veya açmak üzere VBA 'a erişimi etkinleştir

Microsoft Office sistemi projesi için bir Visual Studio Araçları oluşturmadan veya açmadan önce Microsoft Office Visual Basic for Applications (VBA) proje sistemine erişimi açıkça etkinleştirmeniz gerekir.

 Microsoft Office geliştirme projeleri, projeler Excel kullanmasa bile Microsoft Office Word ve Microsoft Office Visual Basic for Applications Visual Basic for Applications (VBA) proje sistemine erişim gerektirir. hem Visual Basic hem de C# projelerindeki denetimlerin tasarım zamanı desteği, Visual Basic for Applications proje sistemine bağlıdır.

 bazı Microsoft Office makro virüsleri, kendilerini yaymaya yönelik bir yol olarak Visual Basic for Applications proje sistemini otomatikleştirmeye çalışır. Visual Basic for Applications proje sistemine erişimi etkinleştirerek, makro virüslerinin yayılmasının önlenmesine yardımcı olan bir korumayı kaldırırsınız. ancak, normal makro güvenliği yerinde kalır, bu nedenle makro güvenlik düzeyi ve Office uygulamalarınız için tuttuğunuz güvenilen yayımcıların listesi bilgisayarınızda herhangi bir makronun çalışıp çalışmadığını tespit eder.

> [!NOTE]
> Bu yalnızca geliştirme bilgisayarı için geçerlidir. son kullanıcı bilgisayarlarında, Office çözümleri çalıştırmak için bu seçeneğin etkinleştirilmesi gerekmez.

 Visual Basic for Applications proje sistemine erişimi devre dışı bırakmak, virüslerden korunmanıza yardımcı olmak önemlidir, ancak bilgisayarınız bir makro virüsü ile bulaşmışsa, bazı virüslerin diğer belgelere yayılmasını durdurmaya yardımcı olur. Bu seçenek, bilgisayarınız için ek bir koruma katmanı olarak varsayılan olarak devre dışıdır, ancak en iyi güvenlik yöntemlerini takip ediyorsanız bilgisayarınızı virüslere açık hale getirir.

 Office makro virüslerine karşı en iyi koruma, yalnızca doğrulanmış, bilinen kaynaklardaki makrolara güvenmek ve güvenlik düzeltme ekleri ve virüs tarayıcıları ile güncel kalmak için Office yüksek veya çok yüksek güvenlik düzeyinde çalıştırılır.

 **Visual Basic Project için güven erişimi** seçeneğini el ile etkinleştirebilir veya devre dışı bırakabilirsiniz.

 VBA veya COM hataları görürseniz Office yüklemenizi onarabilirsiniz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Visual Basic projelerine erişimi etkinleştirmek veya devre dışı bırakmak için

1. **Dosya** sekmesine tıklayın.

2. **Seçenekler**’e tıklayın.

3. **güven merkezi**' ne ve ardından **güven merkezi Ayarlar**' ne tıklayın.

4. **güven merkezi**'nde **makro Ayarlar**' ye tıklayın.

5. Visual Basic projelerine erişimi etkinleştirmek veya devre dışı bırakmak için **VBA proje nesne modeline güven erişimini** işaretleyin veya işaretini kaldırın.

6. **Tamam**'a tıklayın.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office sistemiyle Visual Basic projelerine erişimi etkinleştirmek veya devre dışı bırakmak için

1. Word veya Excel **araçlar** menüsünde, **makro**' ın üzerine gelin ve ardından **güvenlik**' e tıklayın.

2. **Güvenlik** iletişim kutusunda, **Güvenilen Yayımcılar** sekmesine tıklayın.

3. **Visual Basic Project erişimi** devre dışı bırakmak için seçin veya temizleyin.

4. **Tamam**'a tıklayın.

## <a name="to-set-your-office-macro-security-level"></a>Office makro güvenlik düzeyini ayarlamak için

1. **Dosya** sekmesine tıklayın.

2. **Seçenekler**’e tıklayın.

3. **güven merkezi**' ne ve ardından **güven merkezi Ayarlar**' ne tıklayın.

4. **güven merkezi**'nde **makro Ayarlar**' ye tıklayın.

5. **makro Ayarlar** bölümünde istenen ayarı seçin.

6. **Tamam**'a tıklayın.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Office makro güvenlik düzeyini 2007 Microsoft Office sistemiyle ayarlamak için

1. Word veya Excel **araçlar** menüsünde, **makro**' ın üzerine gelin ve ardından **güvenlik**' e tıklayın.

2. **Güvenlik düzeyi** sekmesinde, istenen ayarı seçin.

    **Güvenlik düzeyi** sekmesi her bir düzey hakkındaki ayrıntıları içerir. daha fazla bilgi için Office yardımında "makro güvenlik düzeyleri" konusuna bakın.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>VBA 'yı 2007 Microsoft Office sistemine yüklemek için

1. Denetim Masası 'nda **Program Ekle/** Kaldır veya **Programlar ve Özellikler**' i çalıştırın.

2. **yüklü olan programlar** listesinde Office seçin.

3. **Değiştir**’e tıklayın.

4. **Özellik Ekle veya Kaldır**' ı seçin ve ardından **devam**' a tıklayın.

5. **Uygulamaların gelişmiş özelleştirmesini Seç**' i seçin ve ardından **İleri**' ye tıklayın.

6. **uygulamalar ve araçlar için güncelleştirme seçeneklerini belirleyin** listesinde **Office paylaşılan özellikler** ' i genişletin.

7. **Visual Basic for Applications**' nin yanındaki açılan menüyü açın ve sonra bilgisayarımdan **çalıştır**' a tıklayın.

8. **Devam**’a tıklayın.

9. **Kapat**’a tıklayın.

## <a name="to-repair-your-installation-of-office"></a>Office yüklemenizi onarmak için

1. Denetim Masası 'nda **Program Ekle/** Kaldır veya **Programlar ve Özellikler**' i çalıştırın.

2. **yüklü olan programlar** listesinde Office sürümünüzü seçin.

3. **Değiştir**’e tıklayın.

4. **Yeniden yükle veya Onar**' ı seçin ve ardından **İleri**' ye tıklayın.

5. **Office yüklememdeki hataları algıla ve onar**' ı seçin ve ardından **yükleme**' ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
