---
title: Visual Studio bir depoyu yönetme
titleSuffix: ''
description: git deposu penceresini kullanarak Visual Studio git deposunu yönetin.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1679fa7558eb7e241fe62b1df30e33d5ba6ef5
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264025"
---
# <a name="manage-git-repositories-in-visual-studio"></a>Visual Studio Git depolarını yönetme

Git deposu penceresi, git deponuzu yönetmenize ve takımınızın üzerinde çalıştığı en güncel kalacaklarına odaklanmanıza yardımcı olan tam ekran git deneyimi sağlar. Örneğin, yürütmeleri Cherry-Pick sıfırlamanız, geri döndürmeniz ya da yalnızca yürütme geçmişinizi temizlemeniz gerekebilir. Git deposu penceresi, Dallarınızı görselleştirmek ve yönetmek için de harika bir yerdir.

## <a name="change-the-last-commit-amend"></a>Son işlemeyi değiştirme (düzeltme)

Son yürütmeyi güncelleştirmek git tarafından düzeltme olarak adlandırılır ve çok yaygın bir kullanım durumdur. Bazen yalnızca COMMIT iletinizi güncelleştirmeniz veya bir son dakika değişikliği eklemeniz gerekebilir.

Komut satırında aşağıdaki komutu kullanarak bir işlemeyi değiştirebilirsiniz:

```bash
git commit --amend
```

Git deposu penceresi, tamamlama iletinizi güncelleştirmeyi kolaylaştırır. Son işlemenin kayıt ayrıntılarını açmak için çift tıklayın ve ardından tamamlama iletisinin yanındaki **Düzenle** seçeneğine tıklayın.

:::image type="content" source="media/vs-2022/git-repository-edit-commit.png" alt-text="Bir kayıt iletisini düzenleme ekran görüntüsü." lightbox="media/vs-2022/git-repository-edit-commit.png":::

Kayıt iletinizi düzenledikten sonra, **Düzeltme**' ye tıklayın.

:::image type="content" source="media/vs-2022/git-repository-amend-commit.png" alt-text="Değişiklik d ' ye tıklayarak düzenlenmiş iletiyi kaydetme ekran görüntüsü." lightbox="media/vs-2022/git-repository-amend-commit.png":::

Son işlemenizden kod değişiklikleri eklemeniz gerekiyorsa, bunu yapmak için git değişiklikler penceresini kullanarak, **düzeltme onay kutusunu** işaretleyip yaptığınız değişiklikleri gerçekleştirebilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-amend-commit.png" alt-text="Git değişiklikleri penceresini kullanarak düzeltme kodu değişikliklerinin ekran görüntüsü." lightbox="media/vs-2022/git-changes-amend-commit.png":::

> [!TIP]
> Düzeltme ve geri yazma geçmişi hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanın: [Git araçları-yeniden yazma geçmişi](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

## <a name="merge-commits-squash"></a>İşlemeleri birleştir (Squash)

Bir işleme serisini birleştirmek için git, yürütmelerin tek bir işleme içinde bekletilmesine yönelik bir seçenek sunar. Bu, sık gerçekleştirilen işlemeler yaptığınızda ve uzak bir depoya göndermeden önce temizlemek istediğiniz uzun bir işleme listesi ile sona erdirmek için yararlı olabilir.

Komut satırında aşağıdaki komutu kullanarak iki işlemeyi ele alabilirsiniz:

```bash
git rebase -i HEAD~2
```

Ardından, aşağıda gösterildiği gibi, kaydetme iletisini **sıkıştırarak**, kaydetmek ve güncelleştirmek için **çekmeyi** güncelleştirin:

:::image type="content" source="media/vs-2022/git-repository-squash-cmd.png" alt-text="Squash için güncelleştirme çekmenin ekran görüntüsü." lightbox="media/vs-2022/git-repository-squash-cmd.png":::

Visual Studio yürütmeleri birleştirmek için **Ctrl** tuşunu kullanın ve birleştirmek istediğiniz işlemeleri çoklu seçin. Ardından, sağ tıklayın ve **Squash yürütmelerini** seçin. Visual Studio, kayıt iletilerinizi otomatik olarak birleştirir, ancak bazen güncelleştirilmiş bir ileti sağlanması daha iyidir. Kayıt iletinizi gözden geçirdikten ve güncelleştirdiğinizde, **Squash düğmesine** tıklayın.

:::image type="content" source="media/vs-2022/git-repository-squash-visual-studio.png" alt-text="Visual Studio 'de sıkıştırarak yürütmelerinin ekran görüntüsü." lightbox="media/vs-2022/git-repository-squash-visual-studio.png":::

> [!TIP]
> Aşağıdaki bağlantıyı kullanarak squash ve yeniden yazma geçmişi hakkında daha fazla bilgi edinebilirsiniz: [Git araçları-yeniden yazma geçmişi](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

## <a name="merge-and-rebase-branches"></a>Dalları birleştirin ve yeniden temellendir

Farklı özelliklerle çalışmak için git dalları kullanıyorsanız, bir noktada diğer dallara tanıtılan güncelleştirmeleri dahil etmeniz gerekir. Bu, özellik dalınızda çalışmaya devam ederken veya özellik dalınızda çalışmayı bitirdiğinizde ve farklı bir dala ekleyerek değişikliklerinizi tutmanız gerektiğinde gerçekleşebilir. Git 'de, dalları birleştirerek veya yeniden temelleyerek bunu yapabilirsiniz.

Ana dalı komut satırındaki New_Feature dalına birleştirmek için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git merge main
```

Visual Studio aynı yapmak için dal listesinde çift tıklayarak New_Feature dalı kullanıma alın. Ardından ana öğesine sağ tıklayın ve ' **Ana ' öğesini ' New_Feature ' Içine Birleştir** ' i seçin

:::image type="content" source="media/vs-2022/git-repository-merge-ui.png" alt-text="Visual Studio içindeki birleştirme dallarının ekran görüntüsü.":::

Ana dalı komut satırındaki New_Feature dalına yeniden temellendirmeye yönelik olarak, aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git rebase main
```

Visual Studio aynı yapmak için dal listesinde çift tıklayarak New_Feature dalı kullanıma alın. Ardından Main 'e sağ tıklayın ve ' **New_Feature ' öğesini ' Main ' üzerine yeniden temellendir** seçin

:::image type="content" source="media/vs-2022/git-repository-rebase-ui.png" alt-text="Visual Studio dalların yeniden temellendirmesinin ekran görüntüsü.":::

> [!TIP]
> Genel olarak birleştirme, yeniden temellendirme ve dallanma hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanın: [Git dallandırma](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

## <a name="copy-commits-cherry-pick"></a>İşlemeleri kopyalama (tek tek seçme)

Tek tek seçme kullanarak yürütmeleri bir daldan diğerine kopyalama. Birleştirme veya yeniden temellendirmenin aksine, tek tek seçim, daldaki tüm değişiklikler yerine yalnızca seçtiğiniz yürütmelerden değişiklikleri getirir. Tek tek seçme, bu yaygın sorunların üstesinden gelmenin harika bir yoludur:

- Yanlışlıkla yanlış dala yürütülüyor. Tek tek-değişiklikleri doğru dala göre seçin ve ardından özgün dalı önceki işlemeye sıfırlayın.
- Bir özellik dalında yapılan bir işleme kümesini kullanıma alarak bunları ana dalınızla daha erken birleştirmeniz gerekir.
- Dalınızı yeniden temellendirmeden, ana daldan belirli yürütmelerde taşıma.

Komut satırını kullanarak bir işlemeden değişiklikleri geçerli dalınıza kopyalamak için aşağıdaki komutları kullanın:

```bash
git cherry-pick 7599e530
```

Visual Studio aynı yapmak için, tek bir tıklama ile seçerek bir yürütmeyi seçmek istediğiniz dalı önizleyin. Ardından hedeflenen işlemeye sağ tıklayın ve **tek tek Seç**' i seçin.

:::image type="content" source="media/vs-2022/git-repository-cherry-pick-ui.png" alt-text="Visual Studio ' de tek tek seçme ekran görüntüsü." lightbox="media/vs-2022/git-repository-cherry-pick-ui.png":::

işlem tamamlandıktan sonra, Visual Studio başarılı bir ileti ve seçtiğiniz işleme giden bölümünde gösterilir.

> [!TIP]
> Aşağıdaki bağlantıyı kullanarak tek tek seçme işlemeleri hakkında daha fazla bilgi edinebilirsiniz: [Git tek tek seçme](https://git-scm.com/docs/git-cherry-pick)

## <a name="revert-changes"></a>Değişiklikleri dön

Paylaşılan dallara gönderilen işlemeler üzerinde yapılan değişiklikleri geri almak için geri çevir ' i kullanın. Geri çevir komutu, önceki bir yürütmede yapılan değişiklikleri geri alan yeni bir kayıt oluşturur. Alma, depo geçmişini yeniden yazıp başkalarıyla çalışırken kullanımı güvenli hale getirir.

Komut satırını kullanarak bir işlemede yapılan değişiklikleri dönüştürmek için aşağıdaki komutları kullanın:

```bash
git revert 53333305
git commit
```

Bu komutlar, kayıt 53333305 ' de yapılan değişiklikleri geri alacak ve dalda yeni bir işlem oluşturur. Commit_id konumundaki özgün tamamlama hala git geçmişinde. Visual Studio aynı yapmak için, vermek istediğiniz yürütmeye sağ tıklayın ve bağlam menüsünden **çevir** ' i seçin. eyleminizi onaylayıp işlem tamamlandıktan sonra, Visual Studio başarılı bir ileti gösterir ve giden bölümünde yeni bir işleme gösterilir.

:::image type="content" source="media/vs-2022/git-repository-revert-ui.png" alt-text="Visual Studio ' ın döndürüleceği ekran görüntüsü." lightbox="media/vs-2022/git-repository-revert-ui.png":::

Geri döndürültiğimiz yürütmenin değişikliklerinin geri döndürüldüğünü onaylamak için yeni işlemeye tıklayın.

:::image type="content" source="media/vs-2022/git-repository-revert-confirmation.png" alt-text="Döndürmeyi Onayla işleminin ekran görüntüsü." lightbox="media/vs-2022/git-repository-revert-confirmation.png":::

> [!TIP]
> Değişiklikleri geri alma hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanın: [Git geri döndürme](https://git-scm.com/docs/git-revert)

## <a name="reset-a-branch-to-a-previous-state"></a>Bir dalı önceki durumuna sıfırlama

Yerel deponuzdaki bir dalı önceki bir kaydetmenin içeriğine geri getirmek için Sıfırla ' yı kullanın. Bu, dalınızı sıfırlarken yapılan işlemeden bu yana tüm değişiklikleri atacak.
> [!WARNING]
> Başkalarıyla paylaşılan dallarda sıfırlama kullanmayın. Bunun yerine döndürmeyi kullanın.

Komut satırını kullanarak bir dalı önceki bir duruma sıfırlamak için aşağıdaki komutu kullanın:

```bash
git reset --hard 53333305
```

Komutun **--sabit** bölümü git 'in dosyaları önceki yürütmenin durumuna sıfırlamasını ve hazırlanan değişiklikleri atmasını söyler. Visual Studio aynı yapmak için, dalınızı sıfırlamak istediğiniz yürütmeye sağ tıklayın ve bağlam menüsünden **değişiklikleri sıfırla > sil (--hard)** öğesini seçin.

:::image type="content" source="media/vs-2022/git-repository-reset-ui.png" alt-text="Visual Studio bir dalı sıfırlayın." lightbox="media/vs-2022/git-repository-reset-ui.png":::

> [!TIP]
> Dalları sıfırlama hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanın: [Git Reset](https://git-scm.com/docs/git-reset)

## <a name="next-steps"></a>Sonraki adımlar

yolculuğa devam etmek için [Visual Studio sayfada birleştirme çakışmalarını çözümle](git-resolve-conflicts.md) ' yi ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](../ide/git-with-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)