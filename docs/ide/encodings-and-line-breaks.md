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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd37547d8107cf35991aab684313dbff37adda0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650888"
---
# <a name="encodings-and-line-endings"></a>Kodlamalar ve satır sonları

Aşağıdaki karakterler, Visual Studio 'da satır sonları olarak yorumlanır:

- CR LF: Satır başı + satır besleme, Unicode karakter 000D + 000A

- LF Satır besleme, Unicode karakter 000A

- NEL Sonraki satır, Unicode karakteri 0085

- ÇIKAR Satır ayırıcı, Unicode karakter 2028

- PS Paragraf ayırıcı, Unicode karakter 2029

Diğer uygulamalardan kopyalanmış olan metin özgün kodlamayı ve satır sonu karakterlerini tutar. Örneğin, Not defteri 'nden metin kopyaladığınızda ve Visual Studio 'daki bir metin dosyasına yapıştırdığınızda, metin Notepad 'de bulunan aynı ayarlara sahiptir.

Farklı satır sonu karakterleri olan bir dosyayı açtığınızda tutarsız çizgi kesme karakterlerinin normalleştirilip normalleştirilmeyeceğini ve hangi tür satır sonlarını seçeceğini soran bir iletişim kutusu görebilirsiniz.

## <a name="advanced-save-options"></a>Gelişmiş kaydetme seçenekleri

İstediğiniz satır sonu karakterlerinin türünü öğrenmek için **dosya**  > **Gelişmiş kaydetme seçenekleri** iletişim kutusunu kullanabilirsiniz. Aynı ayarlarla bir dosyanın kodlamasını de değiştirebilirsiniz.

![Gelişmiş kaydetme seçenekleri iletişim kutusu](media/line_endings.png)

> [!NOTE]
> **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** görmüyorsanız, ekleyebilirsiniz. **Araçlar**' ı ve **Özelleştir**' i seçin ve ardından **Komutlar** sekmesini seçin. **Menü çubuğu** açılır listesinde **Dosya**' yı ve ardından **Ekle komut** düğmesini seçin. **Komut Ekle** iletişim kutusunda, **Kategoriler**altında **Dosya**' yı seçin ve ardından **Komutlar** listesinden **Gelişmiş Kaydet seçeneklerini**belirleyin. **Tamam** ' ı seçin ve ardından menüyü menüdeki herhangi bir yere taşımak Için **aşağı taşı** düğmesini seçin. **Özelleştir** iletişim kutusunu kapatmak için **Kapat** ' ı seçin. Daha fazla bilgi için bkz. [menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatif olarak, **dosya**  >  **\<file \> olarak kaydet**' i seçerek **Gelişmiş kaydetme seçenekleri** iletişim kutusuna erişebilirsiniz. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki aşağı açılan üçgeni seçin ve **kodlamayla kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)