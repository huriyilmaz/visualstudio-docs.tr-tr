---
title: "Öğretici: Visual Studio 2019'da bir repodan proje açma"
description: Visual Studio 2019'Azure DevOps git veya Visual Studio açmayı öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389949"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: Bir repodan proje açma

Bu öğreticide, Visual Studio bir depoya ilk kez bağlanacak ve ardından bu depodan bir proje açabilirsiniz.

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

## <a name="open-a-project-from-a-github-repo"></a>GitHub depodan proje açma

Visual Studio 2019'da bir GitHub Visual Studio bir projeyi nasıl açabilirsiniz? Özellikle sürüm [**16.8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklemiş olursanız, bu sürümde yeni, daha tam olarak tümleşik [bir Git Visual Studio](../ide/git-with-visual-studio.md) kullanılabilir.

Ancak, hangi sürümü yüklemiş olur olun, github depodan proje açmak için Visual Studio.

#### <a name="168-and-later"></a>[16.8 ve sonrası](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub depolarını kopyalama ve ardından bir proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Depo Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürüme Git deposu URL'si girmenizi istediğiniz Depoyu Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz.** Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![2019 sürüm 16.8 ve sonraki bir sürüme hesap bilgilerinizi Visual Studio veya düzenley istediğiniz Git Kullanıcı Bilgileri iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya daha sonra İptal'i seçerek bunu seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi için Visual Studio [bakın.](../ide/signing-in-to-visual-studio.md) Ayrıca, oturum açma için GitHub hesabınızla ilgili belirli bilgiler için Bkz. [GitHub hesaplarıyla](../ide/work-with-github-accounts.md) çalışma Visual Studio.

    Ardından Visual Studio otomatik olarak yüklenir ve çözüm depodan açılır.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Visual Studio açık olan Git'te projenin ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer.png )

1. Depoda birden çok çözüm varsa bunları Çözüm Gezgini. Görünüm değiştir düğmesini seçerek çözüm  listesini görüntü Çözüm Gezgini.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Görünümleri Değiştir düğmesi Visual Studio Git'te açık olan bir projenin ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, klasör görünümü'ne kök klasörü açma **veya** açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Görünümleri Değiştir düğmesini seçtikten sonra Git'te açık olan .sln dosyasının ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için Görünümleri Değiştir **düğmesini yeniden** seçin.

    > [!TIP]
    > Depo klonlamak **ve** bir projeyi açmak için Visual Studio IDE'de Git menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub depodan yerel olarak proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin.**

    Visual Studio çözüme veya Dosya Gezgini göz atarak açmak için seçerek bir Dosya Gezgini örneği açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Proje veya çözüm aç' penceresinin ekran görüntüsü](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek** hızlı bir şekilde yeniden açın.

    > [!TIP]
    > Daha önce kopyalanmış bir depodan yerel Visual Studio ve dosyaları açmak için IDE'de **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Yerel Depolar seçeneği genişletilmiş Git menüsünün ekran görüntüsü](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlama!

#### <a name="167-and-earlier"></a>[16.7 ve önceki sürümler](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub depolarını kopyalama ve ardından bir proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Kodu kopyala veya iade edin' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeyi repodan açar.

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![Visual Studio 2019 sürüm 16.7 ve Çözüm Gezgini açılan listesinin ekran görüntüsü](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa açılır menüde "Çözüm Bulunamadı" yazıyor. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

    Kodlamaya başlama!

---

> [!NOTE]
> Visual Studio 2017'ye özgü bilgiler için Visual Studio [2017'de bir repodan proje](tutorial-open-project-from-repo-visual-studio-2017.md) açma sayfasına bakın.

## <a name="connect-to-an-azure-devops-server"></a>Azure DevOps sunucusuna bağlanma

Visual Studio 2019 kullanarak bir Azure DevOps sunucusuna bağlanarak ne göreceğiniz, sahip olduğunuz sürüme bağlıdır. Özellikle, [**sürüm 16.8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklemişsanız, kullanıcı arabirimini Visual Studio'de yeni ve daha tam olarak tümleştirilmiş [bir Git](../ide/git-with-visual-studio.md) deneyimine uyum sağlayacak şekilde Visual Studio.

Ancak, hangi sürümü yüklemiş olur olun, her zaman bir Azure DevOps sunucuya Visual Studio.

#### <a name="168-and-later"></a>[16.8 ve sonrası](#tab/vs168later)

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde depo kopyalama iletişim kutusunun ekran Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

    ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Projeye Bağlan' iletişim kutusunun 'Depoya gözat' bölümünün ekran görüntüsü](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Projeye Bağlan iletişim kutusunda,** bağlanmak istediğiniz bir repo seçin ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Projeye Bağlan' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Bağlanmak için önceden doldurulmuş bir repos listesi görmüyorsanız,  sunucu URL'si girmek için Azure DevOps Server Ekle'yi seçin. (Alternatif olarak, mevcut bir hesap eklemek veya bir Azure DevOps Server hesabı oluşturmak için bağlantılar içeren bir "Sunucu bulunamadı" Azure DevOps olabilir.)

   Ardından Visual Studio ve **Çözüm Gezgini** gösteren bir dosya açılır.

1. Takım Gezgini **eylemlerini** görüntülemek için Azure DevOps seçin.

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Takım Gezgini' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 ve önceki sürümler](#tab/vs167earlier)

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde yer alan 'Depoya göz atma Azure DevOps' bölümünün yer Visual Studio' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Projeye Bağlan iletişim kutusunda,** bağlanmak istediğiniz bir repo seçin ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerden oluşturulan 'Projeye Bağlan' iletişim kutusunun ekran görüntüsü](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

   Visual Studio, **Takım Gezgini** tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki bir sürümde yer alan Takım Gezgini penceresinin ekran görüntüsü](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için Klasör Görünümünü **Göster bağlantısını** seçin.

     ![Takım Gezgini 2019 sürüm 16.7 ve önceki sürümlerindeki Visual Studio penceresinin Çözümler bölümünün ekran görüntüsü](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **,** Çözüm Gezgini.

1. Açılacak **bir çözüm dosyası** (özel olarak bir .sln dosyası) aramak için Çözümler ve Klasörler bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Takım Gezgini 'Çözümler ve Klasörler' bildiriminin ekran görüntüsü](./media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyanız yoksa bir 'Çözüm Bulunamadı' iletisi görüntülenir. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

---

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ile kod vermeye hazırsanız, aşağıdaki dile özgü öğreticilerden herhangi birini gözden alın:

- [Visual Studio öğreticiler | **C#**](./csharp/index.yml)
- [Visual Studio öğreticiler | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticiler | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticiler | **Python**](../python/index.yml)
- [Visual Studio öğreticiler | **JavaScript,** **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'de bir repodan proje açma](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Visual Studio 2019'da yeni Git deneyimi](../ide/git-with-visual-studio.md)
- [Git ile Takım Gezgini yan yana karşılaştırma](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Kullanmaya başlayın ve Azure Repos ile Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Kullanmaya başlayın ile Azure DevOps](/learn/modules/get-started-with-devops/)
