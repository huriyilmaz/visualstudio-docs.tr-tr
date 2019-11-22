---
title: '10. Adım: ek düğmeler ve onay kutusu için kod yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c23dc511f0dd45a9d62715ed74bc6e2a05afa9a6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295800"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10. Adım: Ek Düğmeler ve Onay Kutusu için Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Artık diğer dört yöntemi tamamlamaya hazırsınız. Bu kodu kopyalayabilir ve yapıştırabilirsiniz, ancak bu öğreticiden en iyi şekilde bilgi edinmek istiyorsanız kodu yazın ve IntelliSense kullanın.

 Bu kod, daha önce eklediğiniz düğmelere işlevsellik ekler. Bu kod olmadan düğmeler hiçbir şey yapmaz. Düğmeler, denetimleri etkinleştirdiğinizde farklı şeyler yapmak için `Click` olaylarında kod kullanır (ve onay kutusu `CheckChanged` olayını kullanır). Örneğin, **Resmi Temizle** düğmesini seçtiğinizde etkinleştiren `clearButton_Click` olayı, `Image` özelliğini `null` (veya `nothing`) olarak ayarlayarak geçerli görüntüyü siler. Koddaki her olay kodun ne yaptığını açıklayan yorumlar içerir.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 5](https://go.microsoft.com/fwlink/?LinkId=205216) veya [öğretici 1: video üzerinde C# bir resim görüntüleyici oluşturma 5](https://go.microsoft.com/fwlink/?LinkId=205206). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

> [!NOTE]
> En iyi uygulama olarak: kodunuzda her zaman yorum yapın. Yorumlar, bir kişinin okuması ve kodunuzun daha anlaşılır olması için gereken zamana değecektir. Yorum satırındaki her şey program tarafından yok sayılır. Görselde C#bir satırı, başlangıca iki eğik çizgi (//) yazarak yorum yapın ve Visual Basic tek tırnak işaretiyle (') başlayarak bir satırı açıklama olarak görürsünüz.

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Ek düğmeler ve onay kutusu için kod yazmak için

- Aşağıdaki kodu Form1 kod dosyanıza ekleyin (Form1.cs veya Form1. vb). Visual Basic kodu görüntülemek için **vb** sekmesini seçin.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 11. [Adım: Programınızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md).

- Önceki öğretici adımına dönmek için bkz. 9. [Adım: İnceleme, yorum ve test kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)etme.
