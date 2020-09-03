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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75588596"
---
# <a name="encodings-and-line-endings"></a>Kodlamalar ve satır sonları

Aşağıdaki karakterler, Visual Studio 'da satır sonları olarak yorumlanır:

- CR LF: satır başı + satır besleme, Unicode karakterler 000D + 000A

- LF: satır besleme, Unicode karakter 000A

- NEL: sonraki satır, Unicode karakter 0085

- LS: satır ayırıcı, Unicode karakter 2028

- PS: paragraf ayırıcı, Unicode karakter 2029

Diğer uygulamalardan kopyalanmış olan metin özgün kodlamayı ve satır sonu karakterlerini tutar. Örneğin, Not defteri 'nden metin kopyaladığınızda ve Visual Studio 'daki bir metin dosyasına yapıştırdığınızda, metin Notepad 'de bulunan aynı ayarlara sahiptir.

Farklı satır sonu karakterleri olan bir dosyayı açtığınızda tutarsız çizgi kesme karakterlerinin normalleştirilip normalleştirilmeyeceğini ve hangi tür satır sonlarını seçeceğini soran bir iletişim kutusu görebilirsiniz.

## <a name="advanced-save-options"></a>Gelişmiş kaydetme seçenekleri

İstediğiniz **File**  >  satır sonu karakterlerinin türünü öğrenmek için dosya**Gelişmiş kaydetme seçenekleri** iletişim kutusunu kullanabilirsiniz. Aynı ayarlarla bir dosyanın kodlamasını de değiştirebilirsiniz.

![Gelişmiş kaydetme seçenekleri iletişim kutusu](media/line_endings.png)

> [!NOTE]
> **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** görmüyorsanız, ekleyebilirsiniz. **Araçlar**' ı ve **Özelleştir**' i seçin ve ardından **Komutlar** sekmesini seçin. **Menü çubuğu** açılır listesinde **Dosya**' yı ve ardından **Ekle komut** düğmesini seçin. **Komut Ekle** iletişim kutusunda, **Kategoriler**altında **Dosya**' yı seçin ve ardından **Komutlar** listesinden **Gelişmiş Kaydet seçeneklerini**belirleyin. **Tamam** ' ı seçin ve ardından menüyü menüdeki herhangi bir yere taşımak Için **aşağı taşı** düğmesini seçin. **Özelleştir** iletişim kutusunu kapatmak için **Kapat** ' ı seçin. Daha fazla bilgi için bkz. [menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatif olarak, **Dosya**farklı Kaydet ' i seçerek **Gelişmiş kaydetme seçenekleri** iletişim kutusuna erişebilirsiniz  >  ** \<file\> **. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki aşağı açılan üçgeni seçin ve **kodlamayla kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
