---
title: Kodlama ve satır sonu karakterleri
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588596"
---
# <a name="encodings-and-line-endings"></a>Kodlamalar ve satır sonları

Visual Studio'da satır sonlarını olarak şu karakterleri yorumlanır:

- 000 D + 000A Unicode karakterler, satır başı ve satır besleme CR LF:

- LF: Satır besleme, Unicode karakter 000A

- NEL: Sonraki satır, Unicode karakter 0085

- LS: Unicode karakter 2028 satır ayırıcı

- PS: Paragraf ayırıcı, Unicode karakter 2029

Diğer uygulamalardan kopyaladığınız metin orijinal kodlama ve satır sonu karakterleri korur. Örneğin, Not Defteri'nden metni kopyalayın ve Visual Studio'da bir metin dosyasına yapıştırın, metni Not Defteri'nde olduğu aynı ayarları içerir.

Farklı satır sonu karakterleri olan bir dosyayı açtığınızda, tutarsız satır sonu karakterleri normalleştirilmeli ve seçmek için hangi tür satır sonları olup olmadığını soran bir iletişim kutusu görebilirsiniz.

## <a name="advanced-save-options"></a>Gelişmiş sakla seçenekleri

Kullanabileceğiniz **dosya** > **Gelişmiş kaydetme seçenekleri** istediğiniz satır sonu karakterleri türünü belirlemek için iletişim kutusu. Ayrıca, aynı ayarlarla bir dosyanın kodlamasını değiştirebilirsiniz.

![Gelişmiş Kaydetme Seçenekleri iletişim kutusu](media/line_endings.png)

> [!NOTE]
> Görmüyorsanız **Gelişmiş kaydetme seçenekleri** üzerinde **dosya** menüsünde, ekleyebilir. **Araçlar**' ı ve **Özelleştir**' i seçin ve ardından **Komutlar** sekmesini seçin. **Menü çubuğu** açılır listesinde **Dosya**' yı ve ardından **Ekle komut** düğmesini seçin. İçinde **Add Command** iletişim kutusunun **kategorileri**, seçin **dosya**ve ardından **komutları** listesinde  **Gelişmiş sakla seçenekleri**. Seçin **Tamam** seçip **Aşağı Taşı** komutu menüde herhangi bir yere taşımak için düğme. Seçin **kapatmak** kapatmak için **Özelleştir** iletişim kutusu. Daha fazla bilgi için [menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatif olarak, erişebileceğiniz **Gelişmiş kaydetme seçenekleri** iletişim kutusunu **dosya** > **Kaydet \<dosya\> olarak**. İçinde **dosyayı farklı Kaydet** iletişim kutusunda, açılır üçgeni seçin **Kaydet** düğmesini tıklatın ve seçin **kodlamayla kaydetme**.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
