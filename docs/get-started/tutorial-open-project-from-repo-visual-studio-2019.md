---
title: "Öğretici: Visual Studio 2019'da bir repodan proje açma"
description: Visual Studio 2019'Azure DevOps git veya Visual Studio açmayı öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: 8fa77063e5d440cd22c48da1baff6281f3a191b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144216"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: Bir repodan proje açma

Bu öğreticide, Visual Studio bir depoya ilk kez bağlanacak ve ardından bu depodan bir proje açabilirsiniz.

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

## <a name="open-a-project-from-a-github-repo"></a>GitHub bir GitHub açma

Visual Studio 2019'GitHub kullanarak GitHub bir projeyi açma, sahip olduğunuz sürüme bağlıdır. Özellikle, sürüm [**16.8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklemiş olursanız, bu sürümde yeni, daha tam olarak tümleşik [bir Git Visual Studio](../ide/git-with-visual-studio.md) kullanılabilir.

Ancak, hangi sürümü yüklemiş olur olun, bir projeyi her zaman GitHub bir Visual Studio.

#### <a name="168-and-later"></a>[16.8 ve sonrası](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve sonra bir proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Depo Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürüme Git deposu URL'si girmenizi istediğiniz Depoyu Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz.** Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürüme hesap bilgilerinizi girmeniz veya düzenlemeniz için Git Kullanıcı Bilgileri iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya daha sonra İptal'i seçerek bunu seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi [için](../ide/signing-in-to-visual-studio.md) Visual Studio bakın. Oturum a açma için GitHub hesabınızla çalışma hakkında daha fazla bilgi için GitHub [hesabıyla](../ide/work-with-github-accounts.md) çalışma Visual Studio bakın.

    Ardından Visual Studio otomatik olarak yüklenir ve çözüm depodan açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Çözüm Gezgini Git'te açık olan projenin ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer.png )

1. Depoda birden çok çözüm varsa bunları daha sonra Çözüm Gezgini. Görünüm değiştir düğmesini seçerek çözüm  listesini görüntü Çözüm Gezgini.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Visual Studio Görünüm değiştir düğmesi vurgulanmış şekilde Git'te açık olan bir projenin ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, kök klasörü Klasör Görünümü'ne açma **veya** açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürümde Görünümleri Değiştir düğmesini seçtikten sonra, Çözüm Gezgini'da açık olan Git'te .sln dosyasının ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için Görünümleri Değiştir **düğmesini yeniden** seçin.

    > [!TIP]
    > Depo klonlamak **ve** bir projeyi açmak için Visual Studio IDE'de Git menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin.**

    Visual Studio çözüm veya Dosya Gezgini göz atarak açmak için seçerek bir Dosya Gezgini örneği açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Proje veya çözüm aç' penceresinin ekran görüntüsü](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek** hızlı bir şekilde yeniden açın.

    > [!TIP]
    > Daha önce kopyalanmış bir depodan yerel Visual Studio ve dosyaları açmak için IDE'de **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü, Yerel Depolar seçeneği genişletilmiş](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlama!

#### <a name="167-and-earlier"></a>[16.7 ve önceki sürümler](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve sonra bir proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Kodu kopyala veya iade edin' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeyi repodan açar.

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Çözüm Gezgini açılan listesinin ekran görüntüsü](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa açılır menüde "Çözüm Bulunamadı" yazıyor. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

    Kodlamaya başlama!

---

> [!NOTE]
> Visual Studio 2017'ye özgü bilgiler için Visual Studio [2017'de bir repodan proje](tutorial-open-project-from-repo-visual-studio-2017.md) açma sayfasına bakın.

## <a name="connect-to-an-azure-devops-server"></a>Bağlan sunucuya Azure DevOps yükleme

Visual Studio 2019 kullanarak bir Azure DevOps sunucusuna bağlanarak ne göreceğiniz, sahip olduğunuz sürüme bağlıdır. Özellikle, [**sürüm 16.8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklemiş olursanız, kullanıcı arabirimini Visual Studio'de yeni ve tam olarak tümleştirilmiş bir Git deneyimine uyum [sağlayacak](../ide/git-with-visual-studio.md) şekilde Visual Studio.

Ancak, hangi sürümü yüklemiş olur olur olun, her zaman bir Azure DevOps sunucusuna Visual Studio.

#### <a name="168-and-later"></a>[16.8 ve sonrası](#tab/vs168later)

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Depo Klonla iletişim kutusunun ekran Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

    ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Bağlan'a Project' iletişim kutusunun 'Depoya gözat' bölümünün ekran görüntüsü](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Bağlan bir Project' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Bağlanmak için önceden doldurulmuş bir repos listesi görmüyorsanız,  sunucu URL'si girmek için Azure DevOps Server Ekle'yi seçin. (Alternatif olarak, mevcut bir hesap eklemek veya bir Azure DevOps Server hesabı oluşturmak için bağlantılar içeren bir "Sunucu bulunamadı" Azure DevOps da olabilir.)

   Ardından Visual Studio ve **Çözüm Gezgini** gösteren bir dosya açılır.

1. Eylem **Takım Gezgini** görüntülemek için Azure DevOps seçin.

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Takım Gezgini' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 ve önceki sürümler](#tab/vs167earlier)

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümleri listelene 'Depoya göz atma' bölümüyle 'Kodu kopyala veya teslim alma Azure DevOps' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerden oluşturulan 'Bağlan'a Project' iletişim kutusunun ekran görüntüsü](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

   Visual Studio, **Takım Gezgini** tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki sürümlerindeki uygulama penceresinin ekran görüntüsü](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için Klasör Görünümünü **Göster bağlantısını** seçin.

     ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde, kopyalama tamamlandıktan sonra Takım Gezgini penceresinin Çözümler bölümünün ekran görüntüsü](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **,** Çözüm Gezgini.

1. Açılacak **çözüm dosyasını** (özel olarak bir .sln dosyası) aramak için Çözümler ve Klasörler bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Takım Gezgini 'Çözümler ve Klasörler' bildiriminin ekran görüntüsü](./media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyanız yoksa, 'Çözüm Bulunamadı' iletisi görüntülenir. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

---

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ile kod vermeye hazırsanız, aşağıdaki dile özgü öğreticilerden herhangi birini gözden alın:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript,** **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'de bir repodan proje açma](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Visual Studio 2019'da yeni Git deneyimi](../ide/git-with-visual-studio.md)
- [Git ile Takım Gezgini yan yana karşılaştırma](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Kullanmaya başlayın ve Azure Repos ile Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Kullanmaya başlayın ile Azure DevOps](/learn/modules/get-started-with-devops/)
