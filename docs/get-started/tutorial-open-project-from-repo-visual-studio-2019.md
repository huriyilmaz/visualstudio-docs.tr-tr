---
title: "Öğretici: Visual Studio 2019 ' de bir depoyu bir proje açın"
description: Visual Studio 2019 kullanarak bir git veya Azure DevOps deposunda bir projeyi açmayı öğrenin.
ms.custom: get-started
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
ms.openlocfilehash: 76dcd5061e2e12688f5119598071c3235e620967
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671719"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: bir depodan bir proje açın

Bu öğreticide, bir depoya ilk kez bağlanmak ve ardından bir projeyi açmak için Visual Studio kullanacaksınız.

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

## <a name="open-a-project-from-a-github-repo"></a>GitHub deposundan proje açma

Visual Studio 2019 kullanarak bir GitHub deposundan proje açtığınızda, sahip olduğunuz sürüme göre farklılık gösterir. Özellikle, sürüm [**16,8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklediyseniz, [Visual Studio 'da](../ide/git-with-visual-studio.md) kullanabileceğiniz yeni, daha fazla tam tümleşik git deneyimi vardır.

Ancak hangi sürümü yüklediğinizden bağımsız olarak, Visual Studio ile bir GitHub deposundan her zaman bir projeyi açabilirsiniz.

#### <a name="168-and-later"></a>[16,8 ve üzeri](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub deposunu kopyalayın ve ardından bir proje açın

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu Kopyala iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,8 ve üzeri bir git deposu URL 'SI girdiğiniz depoyu Kopyala iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Kullanıcı oturum açma bilgileriniz, **Git Kullanıcı bilgileri** iletişim kutusunda istenebilir. Bilgilerinizi ekleyebilir ya da sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde hesap bilgilerinizi girdiğiniz veya düzenlediğiniz git Kullanıcı bilgileri iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri Global. gitconfig 'de ayarla dosyanıza eklemek için **Kaydet** ' i seçin. (Veya daha sonra **iptal**' i seçerek bunu yapmayı seçebilirsiniz.)

    > [!TIP]
    > Visual Studio 'da oturum açma hakkında daha fazla bilgi için bkz. [Visual Studio 'Da oturum açma](../ide/signing-in-to-visual-studio.md) sayfası. Ayrıca, GitHub hesabınızı kullanarak oturum açmak için nasıl kullanılacağına ilişkin belirli bilgiler için, [Visual Studio 'Da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md) sayfasına bakın.

    Ardından, Visual Studio otomatik olarak çözümü depodan yükler ve açar.

   ![Git 'teki projenin, Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde Çözüm Gezgini açık olan ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer.png )

1. Deponuz birden çok çözüm içeriyorsa, bunları Çözüm Gezgini görürsünüz. Çözüm Gezgini ' de **görünümleri Değiştir** düğmesini seçerek çözümlerin listesini görüntüleyebilirsiniz.

   ![Git 'te Çözüm Gezgini açık olan, Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde görünümleri Değiştir düğmesi vurgulanmış olan git 'teki projenin ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, **klasör görünümünde** kök klasörü açma veya açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde görünümleri Değiştir düğmesini seçtikten sonra Çözüm Gezgini açık olan git 'teki. sln dosyasının ekran görüntüsü](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için **görünümleri Değiştir** düğmesini yeniden seçin.

    > [!TIP]
    > Ayrıca, bir depoyu kopyalamak ve bir projeyi açmak için Visual Studio IDE 'deki **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerinde git menüsünün ekran görüntüsü](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Önceden kopyalanmış bir GitHub deposundan Yerel olarak proje açma

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde, **Proje veya çözüm aç**' ı seçin.

    Visual Studio, çözüm veya projenize gözatabileceğiniz dosya Gezgini 'nin bir örneğini açar ve ardından onu seçerek açabilirsiniz.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde ' proje veya çözüm aç ' penceresinin ekran görüntüsü](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü kısa süre önce açtıysanız, bunu tekrar **açmak için son** görüntülenen bölümden birini seçin.

    > [!TIP]
    > Ayrıca, daha önce Klonladığınız bir depodan yerel klasörleri ve dosyaları açmak için Visual Studio IDE 'deki **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Yerel depolar seçeneği genişletilmiş olan Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerinde git menüsünün ekran görüntüsü](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlayın!

#### <a name="167-and-earlier"></a>[16,7 ve öncesi](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub deposunu kopyalayın ve ardından bir proje açın

1. Visual Studio 2019 ' i açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluşturma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' kopya veya kullanıma alma kodu ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeden projeyi açar.

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. Bunu seçin ve Visual Studio çözümünüzü açar.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Çözüm Gezgini açılır listesinin ekran görüntüsü](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsü "hiçbir çözüm bulunamadı" ifadesini ifade etmez. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

    Kodlamaya başlayın!

---

> [!NOTE]
> Visual Studio 2017 'e özgü bilgiler için bkz. [Visual Studio 'da bir depodan proje açma 2017](tutorial-open-project-from-repo-visual-studio-2017.md) sayfası.

## <a name="connect-to-an-azure-devops-server"></a>Azure DevOps sunucusuna bağlanma

Visual Studio 2019 kullanarak bir Azure DevOps sunucusuna bağlandığınızda gördükleriniz, sahip olduğunuz sürüme bağlıdır. Özellikle, sürüm [**16,8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklediyseniz, Kullanıcı arabirimini Visual Studio 'Daki [Visual Studio 'da](../ide/git-with-visual-studio.md) yeni, daha tam tümleşik bir git deneyimine uyacak şekilde değiştirdik.

Ancak hangi sürümü yüklediğinizden bağımsız olarak, Visual Studio ile her zaman bir Azure DevOps sunucusuna bağlanabilirsiniz.

#### <a name="168-and-later"></a>[16,8 ve üzeri](#tab/vs168later)

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Azure DevOps için Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu Kopyala iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. **Bir depoya Gözatatıon** bölümünde **Azure DevOps**' u seçin.

    ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde ' projeye Bağlan ' iletişim kutusunun ' bir depoya Gözat ' bölümünün ekran görüntüsü](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' projeye Bağlan ' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Bağlanılacak olan depoların önceden doldurulmuş bir listesini görmüyorsanız sunucu URL 'SI girmek için **Azure DevOps Server Ekle** ' yi seçin. (Alternatif olarak, mevcut bir Azure DevOps Server ekleme veya bir Azure DevOps hesabı oluşturma bağlantıları içeren "sunucu bulunamadı" istemi görebilirsiniz.)

   Daha sonra Visual Studio, klasörleri ve dosyaları gösteren **Çözüm Gezgini** açar.

1. Azure DevOps eylemlerini görüntülemek için **Takım Gezgini** sekmesini seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Takım Gezgini ' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16,7 ve öncesi](#tab/vs167earlier)

1. Visual Studio 2019 ' i açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluşturma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya Gözatatıon** bölümünde **Azure DevOps**' u seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Azure DevOps 'u listeleyen ' bir depoya göz at ' bölümü ile ' kopya veya kullanıma alma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,7 ve öncesinde oluşturulan ' projeye Bağlan ' iletişim kutusunun ekran görüntüsü](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişiminiz olan Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açar ve kopya tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin ekran görüntüsü](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![Kopyalama tamamlandıktan sonra Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin çözümler bölümünün ekran görüntüsü](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açar.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini ' çözümler ve klasörler ' bildiriminin ekran görüntüsü](./media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, ' hiçbir çözüm bulunamadı ' iletisi görüntülenir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

---

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ile kod oluşturmaya hazırsanız, dile özgü aşağıdaki öğreticilerden birine gidin:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript**, **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017 ' de bir depoyu bir projeyi açma](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Visual Studio 2019 'de yeni git deneyimi](../ide/git-with-visual-studio.md)
- [Git ve Takım Gezgini yan yana karşılaştırın](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Azure Repos ve Visual Studio ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps ile çalışmaya başlama](/learn/modules/get-started-with-devops/)