---
title: Kodlama ve satır sonu karakterleri
description: Visual Studio satır sonları olarak yorumladığı karakterler ve özgün kodlama ile satır sonu karakterlerinin nasıl korunacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: db0efa149538d91c5123f6a973d5e8a455ff2e62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094379"
---
# <a name="encodings-and-line-endings"></a>Kodlamalar ve satır sonları

Aşağıdaki karakterler Visual Studio satır sonları olarak yorumlanır:

- CR LF: satır başı + satır besleme, Unicode karakterler 000D + 000A

- LF: satır besleme, Unicode karakter 000A

- NEL: sonraki satır, Unicode karakter 0085

- LS: satır ayırıcı, Unicode karakter 2028

- PS: paragraf ayırıcı, Unicode karakter 2029

Diğer uygulamalardan kopyalanmış olan metin özgün kodlamayı ve satır sonu karakterlerini tutar. örneğin, Not Defteri metin kopyalayıp Visual Studio bir metin dosyasına yapıştırdığınızda, metin Not Defteri aynı ayarlara sahiptir.

Farklı satır sonu karakterleri olan bir dosyayı açtığınızda tutarsız çizgi kesme karakterlerinin normalleştirilip normalleştirilmeyeceğini ve hangi tür satır sonlarını seçeceğini soran bir iletişim kutusu görebilirsiniz.

## <a name="advanced-save-options"></a>Gelişmiş kaydetme seçenekleri

İstediğiniz   >  satır sonu karakterlerinin türünü öğrenmek için dosya **Gelişmiş kaydetme seçenekleri** iletişim kutusunu kullanabilirsiniz. Aynı ayarlarla bir dosyanın kodlamasını de değiştirebilirsiniz.

![Gelişmiş kaydetme seçenekleri iletişim kutusu](media/line_endings.png)

> [!NOTE]
> **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** görmüyorsanız, ekleyebilirsiniz. 
> 1. **Araç** seç, **Özelleştir**, 
> 1. **Komutlar** sekmesini seçin, **menü çubuğu** radyo düğmesini seçin ve ilgili açılan listeden **Dosya**' yı seçin. **Komut Ekle** düğmesini seçin. 
> 1. **Komut Ekle** iletişim kutusunda, **Kategoriler** altında **Dosya**' yı seçin ve ardından **Komutlar** listesinden **Gelişmiş Kaydet seçeneklerini** belirleyin. **Tamam** düğmesini seçin.
> 1. Komutu menüdeki herhangi bir yere taşımak için **Yukarı taşı** ve **aşağı taşı** düğmelerini kullanın. **Özelleştir** iletişim kutusunu kapatmak için **Kapat** ' ı seçin. 
> Daha fazla bilgi için bkz. [menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatif olarak, **Dosya** farklı Kaydet ' i seçerek **Gelişmiş kaydetme seçenekleri** iletişim kutusuna erişebilirsiniz  >  **\<file\>**. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki aşağı açılan üçgeni seçin ve **kodlama ile kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
