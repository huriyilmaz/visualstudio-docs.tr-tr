---
title: Visual Studio'de işleme Visual Studio
titleSuffix: ''
description: Git veya Visual Studio kullanarak bir işleme Azure DevOps.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 85c284f33799239e0409a370d6fa1c43e59dbb5b
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264217"
---
# <a name="make-a-commit-in-visual-studio"></a>Visual Studio'de işleme Visual Studio

Herhangi bir Git iş akışının temel bölümü dosyaları değiştirmek ve bu dosyalarda değişiklikleri işlemektir.

Git, siz çalışırken depoda yapılan dosya değişikliklerini izler ve depoda yer alan dosyaları üç kategoriye ayırıyor. Bu değişiklikler, komut satırına komutu girerken `git status` göreceğiniz değişikliklerle eşdeğerdir:

- **Değiştirilmemiş dosyalar:** Bu dosyalar son işlemeden bu yana değişmemiştir.
- **Değiştirilen dosyalar:** Bu dosyalarda son işlemeden bu yana değişiklikler vardır, ancak bunları henüz bir sonraki işleme için hazırlanmadınız.
- **Aşamalı dosyalar:** Bu dosyalar, sonraki işlemeye eklenecek değişikliklere sahip olur.

Çalışmanızı yaptığınız gibi Visual Studio, Git Değişiklikleri penceresinin Değişiklikler **bölümünde** projenize yapılan dosya **değişikliklerini takip** edin.

:::image type="content" source="media/vs-2022/git-changes-window.png" alt-text="Visual Studio 2022'de Git Değişiklikleri penceresi.":::

Hazır olduğunda değişiklikleri hazır hale eklemek için, aşamaya almak istediğiniz her dosyada (artı) düğmesini seçin veya bir dosyaya sağ tıklar ve ardından **+** Aşama'yı **seçin.** Ayrıca Değişiklikler bölümünün üst kısmında yer alan stage all (plus) düğmesini kullanarak değiştirilen tüm dosyalarınızı **+** tek tıklamayla **da sıralayabilirsiniz.**

Bir değişikliği aşamaya Visual Studio bir **Aşamalı Değişiklikler bölümü** oluşturur. Bir sonraki **işlemeye yalnızca** Aşamalı Değişiklikler bölümündeki değişiklikler eklenir ve Bunu, Commit Staged (İşle Aşamalı) **öğesini seçerek yapabilirsiniz.** Bu eylemin eşdeğer komutu şu `git commit -m "Your commit message"` şekildedir: .

:::image type="content" source="media/vs-2022/git-commit-message.png" alt-text="Visual Studio 2022'de Git işleme iletişim kutusu.":::

Değişiklikler , – (eksi) düğmesine tıklayarak **dastaged** olabilir. Bu eylemin eşdeğer komutu, tek `git reset <file_path>` bir dosyanın hazırlanmamış veya bir dizinde yer alan tüm dosyaların `git reset <directory_path>` hazırsız olarak hazırlanmamıştır.

Ayrıca, hazırlama alanı atlayarak değiştirilen dosyalarınızı hazırlamamayı da seçebilirsiniz. Bu durumda, Visual Studio doğrudan işlemenize olanak sağlar. Yalnızca işleme iletinizi girin ve Ardından Hepsini **İşle'yi seçin.** Bu eylemin eşdeğer komutu şu `git commit -a` şekildedir: .

Visual Studio, Hepsini Commit ve Push ve Commit All ve  Sync kısayollarını kullanarak tek tıklamayla işlemeyi ve **eşitlemeyi de** kolaylaştırır. Değişiklikler ve Aşamalı değişiklikler bölümlerindeki herhangi  bir dosyaya çift tıklarsanız, dosyanın değiştirilmemiş sürümüyle satır satır karşılaştırması yapabilirsiniz. 

:::image type="content" source="media/vs-2022/git-file-version-compare.png" alt-text="Visual Studio 2022'de dosya sürümlerinin satır satır karşılaştırması.":::

Bir Commit 'e çift **Visual Studio,** ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri döndürebilirsiniz, işlemeyi sıfırlayabilirsiniz, işleme iletiyi düzeltebilirsiniz veya işlemede bir etiket oluşturabilirsiniz. Yürütmede değiştirilen bir dosyaya tıklarsanız, Visual Studio ve üst  öğesinin yan yana Fark görünümünü açar.

:::image type="content" source="media/vs-2022/git-branch-commit-details.png" alt-text="Visual Studio 2022'de Commit Details iletişim kutusu.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Uzak [sayfaya itme sayfasını ziyaret](git-push-remote.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](git-with-visual-studio.md)
- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
