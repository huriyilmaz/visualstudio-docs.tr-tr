---
title: Git depolarını Visual Studio
titleSuffix: ''
description: Git Deposu penceresini kullanarak Visual Studio git depolarını yönetin.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
---
# <a name="manage-git-repositories-in-visual-studio"></a>Git depolarını Visual Studio

**Git Deposu penceresi**, Git deposunu yönetmenize ve takımınıza yönelik projelerle ilgili güncel kalmanıza yardımcı olan tam ekran bir Git deneyimi sağlar. Örneğin, işlemeleri sıfırlamanız, geri döndürmeniz veya tek tek seçmeniz ya da yalnızca işleme geçmişinizi temizlemeniz gerekir. Git **Deposu penceresi,** dallarınızı görselleştirmek ve yönetmek için de harika bir yerdir.

Git ile Visual Studio denetimi kolaydır.  Ayrıca, tercih edebilirsiniz Git sağlayıcısıyla uzaktan çalışabilirsiniz( örneğin, GitHub veya Azure DevOps. Veya hiçbir sağlayıcı ile yerel olarak çalışabilirsiniz.  

## <a name="change-the-last-commit-amend"></a>Son işlemeyi değiştirme (değiştirme)

Son işlemenin güncelleştirilerek *güncelleştirilerek* Git'te değiştirilmesi gerekir ve bu yaygın bir kullanım durumu olarak kabul edilecektir. Bazen yalnızca işleme iletinizi güncelleştirmeniz veya son dakika değişikliğini de dahil etmek zorundayabilirsiniz.

Aşağıdaki komutu kullanarak komut satırı üzerinde bir işlemeyi düzeltebilirsiniz:

```bash
git commit --amend
```

**Git Deposu penceresi**, işleme iletinizi güncelleştirmeyi kolaylaştırır. Son işlemenin işleme ayrıntılarını çift tıklayarak açın ve ardından işleme iletisi **yanındaki** Düzenle seçeneğini belirleyin.

:::image type="content" source="media/vs-2022/git-repository-edit-commit.png" alt-text="Bir işleme iletisi düzenleme ekran görüntüsü." lightbox="media/vs-2022/git-repository-edit-commit.png":::

Commit iletinizi düzenlemeyi bitirip Düzelt'i **seçin**.

:::image type="content" source="media/vs-2022/git-repository-amend-commit.png" alt-text="Düzelt'i seçerek düzenlenen bir iletiyi kaydetme ekran görüntüsü." lightbox="media/vs-2022/git-repository-amend-commit.png":::

Son işlemenize kod değişiklikleri dahil etmek gerekirse, bunu Git Değişiklikleri penceresinde **yapabilirsiniz** . Düzelt **onay kutusunu** seçin ve değişikliklerinizi iş yapın.

:::image type="content" source="media/vs-2022/git-changes-amend-commit.png" alt-text="Git Değişiklikleri penceresini kullanarak kod değişikliklerini düzeltme ekran görüntüsü." lightbox="media/vs-2022/git-changes-amend-commit.png":::

Değiştirme hakkında daha fazla bilgi edinmek için [Git web sitesinde Git Araçları -](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) Geçmişi Yeniden Yazma'ya bakın.

## <a name="merge-commits-squash"></a>Birleştirme işlemeleri (squash)

Git, bir dizi işlemeyi birleştirmek için işlemeleri tek bir işlemede aşağı yasla seçeneği sağlar. Sık işlemeler yaptıysanız ve uzak depoya itmeden önce temizlemek istediğiniz uzun bir işleme listesiyle karşısanız bu seçenek yararlı olabilir.

Aşağıdaki komutu kullanarak komut satırına iki işlemeyi ezersiniz:

```bash
git rebase -i HEAD~2
```

Ardından, `pick` 'a `squash`güncelleştirin, kaydedin ve işleme iletiyi güncelleştirin.

:::image type="content" source="media/vs-2022/git-repository-squash-cmd.png" alt-text="Seç'i squash olarak güncelleştirme ekran görüntüsü." lightbox="media/vs-2022/git-repository-squash-cmd.png":::

İşle ilgili Visual Studio birleştirmek için **Ctrl** tuşunu kullanarak birleştirmek istediğiniz birden çok işlemeyi seçin. Ardından sağ tıklayın ve Squash **Commits'i seçin**. Visual Studio işleme iletilerinizi otomatik olarak birleştirir, ancak bazen güncelleştirilmiş bir ileti sağlamak daha iyidir. Commit iletinizi gözden geçirdikten ve güncelleştirdikten sonra, Squash **düğmesini** seçin.

:::image type="content" source="media/vs-2022/git-repository-squash-visual-studio.png" alt-text="Visual Studio'da işlemeleri Visual Studio." lightbox="media/vs-2022/git-repository-squash-visual-studio.png":::

Sayfalama hakkında daha fazla bilgi edinmek için [Git web sitesinde Git Araçları -](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) Geçmişi Yeniden Yazma'ya bakın.

## <a name="merge-and-rebase-branches"></a>Dalları birleştirme ve yenidenbase

Farklı özellikler üzerinde çalışmak için Git dallarını kullanıyorsanız, bir noktada diğer dallara tanıtilen güncelleştirmeleri dahil etmek gerekir. Özellik dalınız üzerinde çalışırken bu durum yaşanabilirsiniz. Özellik dalınız üzerinde çalışmayı tamamlar ve değişikliklerinizi farklı bir dala ekleyerek tutmanız gerekir. Git'te bu güncelleştirmeleri dalları birleştirerek veya yenidenbasing ile  dahil edin.

> [!NOTE]
> Aşağıdaki yönergelerde *, New_Feature* dalı için örnek bir ad olarak aşağıdaki yönergeler 1. Bunu kendi dal adınızla değiştirin.

Ana dalı komut satırı üzerinde özellik dalınıza birleştirmek için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git merge main
```

Aynı şeyi Visual Studio dal listesinde çift tıklayarak özellik dalını kontrol edin. Ardından main'e sağ **tıklayın ve** **'main' öğesini 'ana' ile birleştir'New_Feature seçin**.

:::image type="content" source="media/vs-2022/git-repository-merge-ui.png" alt-text="Visual Studio'de dalları birleştirmenin ekran görüntüsü.":::

Ana dalı komut satırı üzerinde özellik dalınıza yeniden temel olarak kullanmak için aşağıdaki komutları kullanın:

```bash
git checkout New_Feature
git rebase main
```

Aynı şeyi Visual Studio dal listesinde çift tıklayarak özellik dalını kontrol edin. Ardından main'e sağ **tıklayın ve** **'ana' New_Feature'yi yeniden temelle'yi seçin**.

:::image type="content" source="media/vs-2022/git-repository-rebase-ui.png" alt-text="Visual Studio'da dalları yeniden Visual Studio.":::

Birleştirme, yenidenbasing ve genel olarak dallama hakkında daha fazla bilgi edinmek için Git web sitesinde [Git](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) Dallama'ya bakın.

## <a name="copy-commits-cherry-pick"></a>Kopyalama işlemeleri (tek tek seçme)

Tek tek seçme seçeneğini kullanarak işlemeleri bir daldan diğerine kopyalayın. Birleştirme veya yeniden tabanının aksine, tek tek seçme, bir dalda yapılan tüm değişiklikler yerine yalnızca sizin seçerek yaptığınız değişiklikleri getirir. Tek tek seçme, bu yaygın sorunları çözmenin harika bir yolu olabilir:

- Yanlışlıkla yanlış dalda işleme. Değişiklikleri doğru dalda tek tek seçme ve özgün dalı önceki işlemeye sıfırlama.
- Bir özellik dalı içinde yapılan işlemeleri daha önce ana dalınıza geri birleştirin.
- Dalını yeniden temel almadan ana daldan belirli işlemelerde bağlantı noktası.

Komut satırı kullanarak bir işlemeden geçerli dalınıza değişiklikleri kopyalamak için aşağıdaki komutu kullanın:

```bash
git cherry-pick 7599e530
```

Aynı şeyi tek Visual Studio tek tıklamayla seçerek tek bir işlemeden seçmek istediğiniz dalın önizlemesini görebilirsiniz. Ardından hedeflenen işlemeye sağ tıklayın ve Tek **Seçim'i seçin**.

:::image type="content" source="media/vs-2022/git-repository-cherry-pick-ui.png" alt-text="Visual Studio'da tek tek seçmenin ekran görüntüsü." lightbox="media/vs-2022/git-repository-cherry-pick-ui.png":::

İşlem tamamlandığında, Visual Studio iletisi gösterir. Tek tek seçtiğin işleme Giden **bölümünde** görünür.

Tek tek seçme işlemeleri hakkında daha fazla bilgi edinmek için tek tek seçme [komutunun Git web sayfasına bakın](https://git-scm.com/docs/git-cherry-pick).

## <a name="revert-changes"></a>Değişiklikleri geri döndürme

Paylaşılan dallara yapılan işlemelerde yapılan değişiklikleri geri almak için revert komutunu kullanın. Revert komutu, önceki işlemede yapılan değişiklikleri geri alan yeni bir işleme oluşturur. Revert komutu depo geçmişini yeniden yazmaz ve başkalarla çalışırken bunu güvenli bir şekilde kullanabilirsiniz.

Bir işlemede yapılan değişiklikleri komut satırı kullanarak geri dönmek için aşağıdaki komutları kullanın. Örnek kimliği, dalınıza gerçek bir işlemenin kimliğiyle değiştirin.

```bash
git revert 53333305
git commit
```

Önceki örnekte, komutlar işlemede yapılan değişiklikleri geri 53333305 ve dalda yeni bir işleme oluşturacak. Özgün işleme hala Git geçmişindedir. Aynı işlemi bu Visual Studio geri almak istediğiniz işlemeye sağ tıklayın ve geri döndür'ü **seçin**. Eyleminizi onaylandıktan ve işlem tamamlandıktan sonra, Visual Studio iletisi görüntülenir ve Giden bölümünde yeni **bir işleme görüntülenir**.

:::image type="content" source="media/vs-2022/git-repository-revert-ui.png" alt-text="Önceki sürümlerde geri döndürmenin Visual Studio." lightbox="media/vs-2022/git-repository-revert-ui.png":::

Geri döndürülen işlemenin değişikliklerini geri almak için yeni işlemeyi seçin.

:::image type="content" source="media/vs-2022/git-repository-revert-confirmation.png" alt-text="Geri döndürme işlemini onaylama işleminin ekran görüntüsü." lightbox="media/vs-2022/git-repository-revert-confirmation.png":::

Değişiklikleri geri döndürme hakkında daha fazla bilgi edinmek için revert [komutunun Git web sayfasına bakın](https://git-scm.com/docs/git-revert).

## <a name="reset-a-branch-to-a-previous-state"></a>Bir dalı önceki bir durumuna sıfırlama

Yerel depoda bir dalı önceki işlemenin içeriğine geri getirmek için reset komutunu kullanın. Bu eylem, dalını sıfırlamak için yaptığınız işlemeden bu yana olan tüm değişiklikleri atar.

> [!WARNING]
> Diğer kişilerin çalışmalarını silebilirsiniz, çünkü paylaşılan dalları sıfırlamayın. Bunun yerine revert komutunu kullanın.

Komut satırı kullanarak bir dalı önceki bir durumuna sıfırlamak için aşağıdaki komutu kullanın. Örnek kimliği, dalınıza gerçek bir işlemenin kimliğiyle değiştirin.

```bash
git reset --hard 53333305
```

Komutun `--hard` bölümü Git'e dosyaları önceki işlemenin durumuna sıfırlaması ve tüm aşamalı değişiklikleri attırmalarını söyler. Aynı şeyi Visual Studio dalını  >  sıfırlamak istediğiniz işlemeye sağ tıklayın ve ardından Değişiklikleri Sıfırla **(--sabit)'i seçin**.

:::image type="content" source="media/vs-2022/git-repository-reset-ui.png" alt-text="Uygulama içinde bir dalı sıfırlamayı gösteren Visual Studio." lightbox="media/vs-2022/git-repository-reset-ui.png":::

Dalları sıfırlama hakkında daha fazla bilgi edinmek için sıfırlama komutu [için Git web sayfasına bakın](https://git-scm.com/docs/git-reset).

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için bkz[. Birleştirme çakışmalarını Visual Studio](git-resolve-conflicts.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](git-with-visual-studio.md)
- [Visual Studio ve GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
