---
title: Bir Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git Deposu penceresini kullanarak Visual Studio git depolarını yönetin.
ms.date: 11/05/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: c6f01cc5532354c371e9f0e9029244d53433ff6e
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002522"
---
# <a name="manage-git-repositories-in-visual-studio"></a>Git depolarını Visual Studio

Git Deposu penceresi, Git deposunu yönetmenize ve takımınız üzerinde çalışmaya devam etmeye odaklanmaya odaklanan tam ekran bir Git deneyimi sağlar. Örneğin, işlemeleri sıfırlamanız, geri döndürmeniz, Cherry-Pick veya yalnızca işleme geçmişinizi temizlemeniz gerekir. Git deposu penceresi, dallarınızı görselleştirmek ve yönetmek için de harika bir yerdir.

## <a name="change-the-last-commit-amend"></a>Son işlemeyi değiştirme (Düzeltme)

Son işlemeyi güncelleştirmek Git tarafından Düzeltme olarak adlandırılır ve bu çok yaygın bir kullanım durumudır. Bazen yalnızca işleme iletinizi güncelleştirmeniz veya son dakika değişikliğini de dahil etmek zorundayabilirsiniz.

Aşağıdaki komutu kullanarak komut satırlarında bir işlemeyi düzeltebilirsiniz:

```bash
git commit --amend
```

Git deposu penceresi, işleme iletinizi güncelleştirmeyi kolaylaştırır. Son işlemenin işleme ayrıntılarını açmak için son işlemeye çift tıklayın ve işleme iletisi **yanındaki** Düzenle seçeneğine tıklayın.

:::image type="content" source="media/vs-2022/git-repository-edit-commit.png" alt-text="Bir işlemeyi düzenleme iletisi ekran görüntüsü":::

Commit iletinizi düzenlemeyi tamamlasanız, Düzelt'e **tıklayın.**

:::image type="content" source="media/vs-2022/git-repository-amend-commit.png" alt-text="Düzelt'e tıklayarak düzenlenen iletiyi kaydetme ekran görüntüsü":::

Son işlemenize kod değişiklikleri dahil etmek gerekirse, Değiştir onay kutusunu işaretleyin ve  değişikliklerinizi işleerek bunu yapmak için Git Değişiklikleri penceresini kullanabilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-amend-commit.png" alt-text="Git Değişiklikleri penceresini kullanarak kod değişikliklerini düzeltme ekran görüntüsü":::

> [!TIP]
> Geçmişi Değiştirme ve Yeniden Yazma hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanabilirsiniz: [Git Araçları - Geçmişi Yeniden Yazma](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

## <a name="merge-commits-squash"></a>Birleştirme işlemeleri (Squash)

Git, bir dizi işlemeyi birleştirmek için işlemeleri tek bir işlemede aşağı yasla seçeneği sağlar. Sık işlemeler yaptıysanız ve uzak depoya itmeden önce temizlemek için uzun bir işleme listesiyle karşısanız bu yararlı olabilir.

Aşağıdaki komutu kullanarak komut satırına iki işlemeyi ezersiniz:

```bash
git rebase -i HEAD~2
```

Ardından burada **gösterildiği gibi** **seçim seçimlerini** güncelleştirin, kaydedin ve işleme iletiyi güncelleştirin:

:::image type="content" source="media/vs-2022/git-repository-squash-cmd.png" alt-text="Güncelleştirmeyi seç'in squash'inin ekran görüntüsü":::

İşle ilgili Visual Studio birleştirmek için **Ctrl** tuşunu kullanın ve birleştirmek istediğiniz işlemeleri çoklu seçin. Ardından sağ tıklayın ve Squash **Commits 'i seçin.** Visual Studio işleme iletilerinizi otomatik olarak birleştirir, ancak bazen güncelleştirilmiş bir ileti sağlamak daha iyidir. Commit iletinizi gözden geçirtikten ve güncelleştirin, sonra **Dazla düğmesine tıklayın.**

:::image type="content" source="media/vs-2022/git-repository-squash-visual-studio.png" alt-text="Visual Studio'daki squash commit'lerinin ekran görüntüsü":::

> [!TIP]
> Geçmişi Squash ve Yeniden Yazma hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanabilirsiniz: [Git Araçları - Geçmişi Yeniden Yazma](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)

## <a name="merge-and-rebase-branches"></a>Dalları birleştirme ve yenidenbase

Farklı özellikler üzerinde çalışmak için Git dalları kullanıyorsanız, bir noktada diğer dallara tanıtilen güncelleştirmeleri dahil etmek gerekir. Bu durum, özellik dalınız üzerinde çalışırken veya özellik dalınız üzerinde çalışmayı bitirerek ve değişikliklerinizi farklı bir dala ekleyerek tutmanız gerekirken olabilir. Git'te dalları birleştirerek veya yenidenbasing ile bunu yapabiliriz.

Ana dalı komut New_Feature dalı ile birleştirmek için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git merge main
```

Aynı şeyi daha sonra Visual Studio dal listesinde New_Feature tıklayarak dalı kontrol edin. Ardından main'e sağ tıklayın ve **'main' öğesini 'ana' ile birleştir'New_Feature' seçin**

:::image type="content" source="media/vs-2022/git-repository-merge-ui.png" alt-text="Visual Studio'da dalları birleştirme ekran görüntüsü":::

Ana dalı komut satırı New_Feature dalı olarak yeniden temele etmek için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git rebase main
```

Aynı şeyi aynı Visual Studio dal listesinde New_Feature tıklayarak dalı teslim edin. Ardından main'e sağ tıklayın ve **'New_Feature' öğesini yeniden temelle'yi seçin**

:::image type="content" source="media/vs-2022/git-repository-rebase-ui.png" alt-text="Visual Studio'de dalları yeniden Visual Studio":::

> [!TIP]
> Genel olarak Birleştirme, Yeniden Tabanı ve Dallanma hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı [kullanabilirsiniz: Git Dallanma](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

## <a name="copy-commits-cherry-pick"></a>Kopyalama işlemeleri (Tek Tek Seçme)

Tek tek seçme kullanarak işlemeleri bir daldan diğerine kopyalayın. Birleştirme veya yenidenbase'den farklı olarak tek tek seçme, bir dalda yapılan tüm değişiklikler yerine yalnızca sizin seçerek yaptığınız değişiklikleri getirir. Tek tek seçme, bu yaygın sorunları çözmenin harika bir yolu olabilir:
- Yanlışlıkla yanlış dalda işleme. Değişiklikleri doğru dala tek tek seçin ve özgün dalı önceki işlemeye sıfırlayın.
- Bir özellik dalı içinde yapılan işlemeleri daha önce ana dalınıza geri birleştirin.
- Dalını yeniden temel almadan ana daldan belirli işlemelerde bağlantı noktası.

Komut satırı kullanarak bir işlemeden geçerli dalınıza değişiklikleri kopyalamak için aşağıdaki komutları kullanın:

```bash
git cherry-pick 7599e530
```

Aynı şeyi Visual Studio tek tıklamayla seçerek tek bir işleme seçmek istediğiniz dalın önizlemesini görebilirsiniz. Ardından hedeflenen işlemeye sağ tıklayın ve tek tek **seçin.**

:::image type="content" source="media/vs-2022/git-repository-cherry-pick-ui.png" alt-text="Visual Studio'de tek tek seçmenin ekran Visual Studio":::

İşlem tamamlandıktan sonra, Visual Studio bir başarı iletisi ve tek tek seçtiğiniz işleme giden bölümde gösterir.

> [!TIP]
> Tek tek seçme işlemeleri hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanabilirsiniz: [Git Tek tek seçme](https://git-scm.com/docs/git-cherry-pick)

## <a name="revert-changes"></a>Değişiklikleri geri döndürme

Paylaşılan dallara yapılan işlemelerde yapılan değişiklikleri geri almak için Geri Döndür'ü kullanın. Revert komutu, önceki işlemede yapılan değişiklikleri geri alan yeni bir işleme oluşturur. Revert, depo geçmişini yeniden yazmaz ve başkalarla çalışırken güvenli bir şekilde kullanılabilir.

Komut satırı kullanılarak bir işlemede yapılan değişiklikleri geri dönmek için aşağıdaki komutları kullanın:

```bash
git revert 53333305
git commit
```

Bu komutlar, işleme komutlarında yapılan 53333305 ve dalda yeni bir işleme oluşturacak. Başlangıçtaki işleme commit_id git geçmişindedir. Aynı işlemi Visual Studio geri dönmek istediğiniz işlemeye sağ tıklayın ve bağlam menüsünden **Geri Döndür'ü** seçin. Eyleminizi onaylayın ve işlem tamamlandıktan sonra, Visual Studio başarılı iletisi ve giden bölümde yeni bir işleme gösterir.

:::image type="content" source="media/vs-2022/git-repository-revert-ui.png" alt-text="Visual Studio'de geri döndürme ekran görüntüsü":::

Yeni işlemeye tıklar ve geri döndürttgız işlemenin değişikliklerini geri aldırmış olduğunu onaylayın.

:::image type="content" source="media/vs-2022/git-repository-revert-confirmation.png" alt-text="Geri döndürme işlemini onaylama işleminin ekran görüntüsü":::

> [!TIP]
> Değişiklikleri geri döndürme hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanabilirsiniz: [Git Revert](https://git-scm.com/docs/git-revert)

## <a name="reset-a-branch-to-a-previous-state"></a>Bir dalı önceki bir durumuna sıfırlama

Yerel depoda bir dalı önceki işlemenin içeriğine geri getirmek için sıfırlamayı kullanın. Dalını sıfırlayılan işlemeden bu yana bu yalnızca tüm değişiklikleri atar.
> [!WARNING]
> Diğerleriyle paylaşılan dallarda Sıfırla'yı kullanma. Bunun yerine Revert kullanın.

Komut satırı kullanarak bir dalı önceki bir durumuna sıfırlamak için aşağıdaki komutu kullanın:

```bash
git reset --hard 53333305
```

Komutun **--hard** bölümü Git'e dosyaları önceki işlemenin durumuna sıfırlaması ve tüm aşamalı değişiklikleri attırmalarını söyler. Aynı şeyi Visual Studio dalını sıfırlamak istediğiniz işlemeye sağ tıklayın ve bağlam menüsünden Değişiklikleri **> (--sabit)** öğesini seçin.

:::image type="content" source="media/vs-2022/git-repository-reset-ui.png" alt-text="Visual Studio'de bir dalı sıfırlama":::

> [!TIP]
> Dalları sıfırlama hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı kullanabilirsiniz: [Git Sıfırlama](https://git-scm.com/docs/git-reset)

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için bu [sayfada birleştirme çakışmalarını Visual Studio](git-resolve-conflicts.md) ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](../ide/git-with-visual-studio.md)