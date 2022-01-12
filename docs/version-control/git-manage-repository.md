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
ms.openlocfilehash: c95a6883031294121b6df1e6b160ef5afde823fc
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534072"
---
# <a name="manage-git-repositories-in-visual-studio"></a>Visual Studio Git depolarını yönetme

**Git deposu** penceresi, git deponuzu yönetmenize ve takımınızın projeleriyle güncel kalmanıza yardımcı olan tam ekran git deneyimi sağlar. Örneğin, yürütmeleri sıfırlamanız, geri döndürmeniz veya tek tek seçmeniz ya da yalnızca yürütme geçmişinizi temizlemeniz gerekebilir. **Git deposu** penceresi, Dallarınızı görselleştirmek ve yönetmek için de harika bir yerdir.

## <a name="change-the-last-commit-amend"></a>Son işlemeyi değiştirme (düzeltme)

Son yürütmeyi güncelleştirmek git 'te *Düzeltme* olarak adlandırılır ve bu, yaygın olarak kullanılan bir kullanım durumdur. Bazen yalnızca COMMIT iletinizi güncelleştirmeniz veya bir son dakika değişikliği eklemeniz gerekebilir.

Komut satırında aşağıdaki komutu kullanarak bir işlemeyi düzeltebilirsiniz:

```bash
git commit --amend
```

**Git deposu** penceresi, tamamlama iletinizi güncelleştirmeyi kolaylaştırır. Son kaydın kayıt ayrıntılarını çift tıklayarak açın ve ardından, tamamlama iletisinin yanındaki **Düzenle** seçeneğini belirleyin.

:::image type="content" source="media/vs-2022/git-repository-edit-commit.png" alt-text="Bir tamamlama iletisini düzenlemenin ekran görüntüsü." lightbox="media/vs-2022/git-repository-edit-commit.png":::

Kayıt iletinizi düzenlemenizi bitirdiğinizde, Değiştir ' **i seçin.**

:::image type="content" source="media/vs-2022/git-repository-amend-commit.png" alt-text="Değiştirilmiş bir iletinin kayıt ekran görüntüsü Değiştir ' i seçin." lightbox="media/vs-2022/git-repository-amend-commit.png":::

Son yürütmeniz için kod değişiklikleri eklemeniz gerekiyorsa, bunu **Git değişiklikleri** penceresinde yapabilirsiniz. Değiştir onay **kutusunu seçin** ve ardından değişikliklerinizi kaydedin.

:::image type="content" source="media/vs-2022/git-changes-amend-commit.png" alt-text="Git değişiklikleri penceresini kullanarak kod değişikliklerinin düzeltme görüntüsü." lightbox="media/vs-2022/git-changes-amend-commit.png":::

Düzeltme hakkında daha fazla bilgi için bkz. git araçları-git Web sitesinde [yeniden yazma geçmişi](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) .

## <a name="merge-commits-squash"></a>İşlemeleri birleştir (Squash)

Bir işleme serisini birleştirmek için git, yürütmelerin tek bir işleme içinde bekletilmesine yönelik bir seçenek sunar. Bu seçenek, bir uzak depoya göndermeden önce, temizlemek istediğiniz uzun bir yürütme listesi ile sık yapılan yürütmeler yaparsanız ve bu seçeneği yararlı olabilir.

Aşağıdaki komutu kullanarak komut satırında iki işlemeyi ele alabilirsiniz:

```bash
git rebase -i HEAD~2
```

Ardından `pick` `squash` , kaydetme iletisini güncelleştirin, kaydedin ve güncelleştirin.

:::image type="content" source="media/vs-2022/git-repository-squash-cmd.png" alt-text="Hazırlama için çekmeyi güncelleştirme ekran görüntüsü." lightbox="media/vs-2022/git-repository-squash-cmd.png":::

Visual Studio yürütmeleri birleştirmek için, birleştirmek istediğiniz birden çok işlemeyi seçmek üzere **Ctrl** tuşunu kullanın. Ardından sağ tıklayıp **Squash yürütmelerini** seçin. Visual Studio, kayıt iletilerinizi otomatik olarak birleştirir, ancak bazen güncelleştirilmiş bir ileti sağlamak daha iyidir. Kayıt iletinizi gözden geçirdikten ve güncelleştirdikten sonra, **Squash** düğmesini seçin.

:::image type="content" source="media/vs-2022/git-repository-squash-visual-studio.png" alt-text="Visual Studio yürütmelerin ekran görüntüsü." lightbox="media/vs-2022/git-repository-squash-visual-studio.png":::

Ele alma hakkında daha fazla bilgi edinmek için git [araçları-git Web sitesinde yeniden yazma geçmişi](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) bölümüne bakın.

## <a name="merge-and-rebase-branches"></a>Dalları birleştirin ve yeniden temellendir

Farklı özelliklerle çalışmak için git dalları kullanıyorsanız, bazı durumlarda diğer dallara sunulan güncelleştirmeleri dahil etmeniz gerekir. Özellik dalınızda çalışmaya devam ediyorsanız bu durum ortaya çıkabilir. Ayrıca, özellik dalınızda çalışmayı bitirdiğinizde ve farklı bir dala ekleyerek değişikliklerinizi tutmanız gerektiğinde de gerçekleşebilir. Git 'te, dalları birleştirerek veya yeniden temelleyerek bu güncelleştirmeleri dahil edebilirsiniz.

> [!NOTE]
> Aşağıdaki yönergeler, bir özellik dalı için örnek adı olarak *New_Feature* kullanır. Bunu kendi dalınızın adıyla değiştirin.

Ana dalı komut satırındaki özellik dalınızla birleştirmek için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git merge main
```

Visual Studio aynı yapmak için, dal listesinde çift tıklayarak özellik dalına göz atın. Sonra **ana** ' a sağ tıklayın ve ' **ana ' ' New_Feature ' içine Birleştir**' i seçin.

:::image type="content" source="media/vs-2022/git-repository-merge-ui.png" alt-text="Visual Studio dal birleştirme ekran görüntüsü.":::

Komut satırında, ana dalı Özellik dalınızla yeniden temellendirmeye yönelik olarak, aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git rebase main
```

Visual Studio aynı yapmak için, dal listesinde çift tıklayarak özellik dalına göz atın. Ardından **Main** öğesine sağ tıklayın ve ' **New_Feature ' öğesini ' Main ' üzerinde yeniden temellendir**' ı seçin.

:::image type="content" source="media/vs-2022/git-repository-rebase-ui.png" alt-text="Visual Studio dalların yeniden temellendirmesinin ekran görüntüsü.":::

Genel olarak birleştirme, yeniden alma ve dallandırma hakkında daha fazla bilgi edinmek için git Web sitesinde [Git dallandırma](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) bölümüne bakın.

## <a name="copy-commits-cherry-pick"></a>İşlemeleri kopyalama (tek tek seçme)

Tek tek seçme seçeneğini kullanarak yürütmeleri bir daldan diğerine kopyalayın. Birleştirme veya yeniden temellendirmenin aksine, tek tek seçme, bir daldaki tüm değişiklikler yerine yalnızca seçtiğiniz işlemelerin yaptığı değişiklikleri getirir. Tek tek seçme, bu yaygın sorunların üstesinden gelmenin harika bir yoludur:

- Yanlışlıkla yanlış dala yürütülüyor. Tek tek-değişiklikleri doğru dala kadar seçin ve ardından özgün dalı önceki işlemeye sıfırlayın.
- Bir özellik dalında yapılan bir işleme kümesini kullanıma alarak bunları ana dalınızla daha erken birleştirmeniz gerekir.
- Dalınızı yeniden temellendirmeden, ana daldan belirli yürütmelerde taşıma.

Komut satırını kullanarak bir işlemeden değişiklikleri geçerli dalınıza kopyalamak için aşağıdaki komutu kullanın:

```bash
git cherry-pick 7599e530
```

Visual Studio aynı yapmak için, tek bir tıklama ile seçerek bir yürütmeyi seçmek istediğiniz dalı önizleyin. Ardından hedeflenen işlemeye sağ tıklayıp **tek tek** Seç ' i seçin.

:::image type="content" source="media/vs-2022/git-repository-cherry-pick-ui.png" alt-text="Visual Studio ' de tek tek seçme ekran görüntüsü." lightbox="media/vs-2022/git-repository-cherry-pick-ui.png":::

işlem tamamlandığında, Visual Studio başarılı bir ileti gösterir. Seçtiğiniz kayıt **giden** bölümünde görüntülenir.

Tek tek çekme işlemleri hakkında daha fazla bilgi edinmek için, [tek tek seçme komutuna git Web sayfasına](https://git-scm.com/docs/git-cherry-pick)bakın.

## <a name="revert-changes"></a>Değişiklikleri dön

Paylaşılan dallara gönderilen işlemeler üzerinde yapılan değişiklikleri geri almak için geri al komutunu kullanın. Geri çevir komutu, önceki bir yürütmede yapılan değişiklikleri geri alan yeni bir kayıt oluşturur. Bu komut, diğer kişilerle çalışırken kullanımını güvenli hale getiren depo geçmişini yeniden yazmaz.

Bir yürütmede yapılan değişiklikleri komut satırını kullanarak dönüştürmek için aşağıdaki komutları kullanın. Örnek KIMLIĞI, dalınızdaki gerçek bir kaydetmenin KIMLIĞIYLE değiştirin.

```bash
git revert 53333305
git commit
```

Önceki örnekte, komutlar, kayıt 53333305 ' de yapılan değişiklikleri geri alır ve dalda yeni bir işlem oluşturur. Özgün tamamlama hala git geçmişinde. Visual Studio aynı yapmak için, vermek istediğiniz yürütmeye sağ tıklayın ve ardından **çevir**' i seçin. eyleminizi doğruladıktan ve işlem tamamlandıktan sonra, Visual Studio başarılı bir ileti görüntüler ve **giden** bölümünde yeni bir işleme görüntülenir.

:::image type="content" source="media/vs-2022/git-repository-revert-ui.png" alt-text="Visual Studio geri döndürmesinin ekran görüntüsü." lightbox="media/vs-2022/git-repository-revert-ui.png":::

Geri döndürülen yürütmenin değişikliklerinin geri döndürüldüğünü onaylamak için yeni yürütmeyi seçin.

:::image type="content" source="media/vs-2022/git-repository-revert-confirmation.png" alt-text="Bir döndürmeyi onaylama işleminin ekran görüntüsü." lightbox="media/vs-2022/git-repository-revert-confirmation.png":::

Değişiklikleri geri alma hakkında daha fazla bilgi edinmek için [geri çevir komutuna git Web sayfasına](https://git-scm.com/docs/git-revert)bakın.

## <a name="reset-a-branch-to-a-previous-state"></a>Bir dalı önceki durumuna sıfırlama

Yerel deponuzdaki bir dalı önceki bir kaydetmenin içeriğine geri getirmek için reset komutunu kullanın. Bu eylem, dalınızı sıfırlarken yaptığınız işlemeden bu yana gerçekleşen tüm değişiklikleri atar.

> [!WARNING]
> Diğer insanların işini silebileceğinden paylaşılan dalları sıfırlamadınız. Bunun yerine, döndürülüyor komutunu kullanın.

Komut satırını kullanarak bir dalı önceki bir duruma sıfırlamak için aşağıdaki komutu kullanın. Örnek KIMLIĞI, dalınızdaki gerçek bir kaydetmenin KIMLIĞIYLE değiştirin.

```bash
git reset --hard 53333305
```

`--hard`Komutun bölümü git 'in dosyaları önceki yürütmenin durumuna sıfırlamasını ve hazırlanan değişiklikleri atmasını söyler. Visual Studio aynı yapmak için, dalınızı sıfırlamak istediğiniz yürütmeye sağ tıklayın ve sonra silme değişikliklerini **sıfırla**' yı  >  **(--hard)** seçin.

:::image type="content" source="media/vs-2022/git-repository-reset-ui.png" alt-text="Visual Studio bir dalı sıfırlamayı gösteren ekran görüntüsü." lightbox="media/vs-2022/git-repository-reset-ui.png":::

Dalları sıfırlama hakkında daha fazla bilgi edinmek için, [Reset komutu Için git Web sayfasına](https://git-scm.com/docs/git-reset)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için bkz. [Visual Studio birleştirme çakışmalarını çözün](git-resolve-conflicts.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](git-with-visual-studio.md)
- [Visual Studio ve GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
