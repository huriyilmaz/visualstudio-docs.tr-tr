---
title: Ekip Gezgini'nde projelere bağlanma
description: projeleri geliştirmek ve yönetmek üzere takım üyeleriyle çalışmak için Visual Studio Takım Gezgini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: <=vs-2019
ms.openlocfilehash: 1a5191febfa4913316e120ef5d4c0d3fdf2f48bc3d44b68594580800b730d4a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121233933"
---
# <a name="connect-to-projects-in-team-explorer"></a>Ekip Gezgini'nde projelere bağlanma

::: moniker range="vs-2017"

Bir proje geliştirmek ve size, takımınızı ya da projelerinize atanan işleri yönetmek için, **Takım Gezgini** araç penceresini diğer takım üyeleriyle koordine etmek için kullanın. **Takım Gezgini** Visual Studio Git ve GitHub depolara, Team Foundation sürüm denetimi (tfvc) depolarına ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/index-all) (eski adıyla TFS) barındırılan projelere bağlanır. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

Takım Gezgini, Team Foundation sürüm denetimi (tfvc) depolarına ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) ya da şirket içi [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (eski adıyla TFS) barındırılan projelere Visual Studio bağlanır. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

> [!IMPORTANT]
> Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history)sürümü ile Git sürüm denetimi deneyimi varsayılan olarak açık olur. Takım Gezgini ile nasıl Karşılaştırıldığı hakkında daha fazla bilgi edinmek istiyorsanız [**Git ve Takım Gezgini sayfasının yan yana karşılaştırmasını**](../version-control/git-team-explorer-feature-comparison.md) inceleyin.
>
> Ancak Takım Gezgini kullanmaya devam etmeyi tercih ediyorsanız, **Araçlar** > **Seçenekler** > **ortam** > **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açın.

bir projeye bağlanmak için Takım Gezgini kullandığınızda, kullanmakta olduğunuz Visual Studio 2019 sürümüne göre değişir.

## <a name="in-version-168-and-later"></a>Sürüm 16,8 ve üzeri sürümlerde

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Azure DevOps için Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu kopyala iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

    ![Visual Studio 2019 sürüm 16,8 ve sonrasında ' Bağlan Project ' iletişim kutusunun ' depoya gözatatıon ' bölümünün ekran görüntüsü](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > bağlanılacak olan depoların önceden doldurulmuş bir listesini görmüyorsanız sunucu URL 'si girmek için **Azure DevOps Server ekle** ' yi seçin. (alternatif olarak, var olan bir Azure DevOps Server ekleme veya Azure DevOps hesabı oluşturma bağlantıları içeren "sunucu bulunamadı" istemi görebilirsiniz.)

   sonra, Visual Studio klasörleri ve dosyaları gösteren **Çözüm Gezgini** açar.

1. Azure DevOps eylemlerini görüntülemek için **Takım Gezgini** sekmesini seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Takım Gezgini ' iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>Sürüm 16,7 ve önceki sürümlerde

1. Visual Studio 2019 ' i açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluştur ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Azure DevOps listeleyen ' bir depoya göz at ' bölümü ile ' kopya veya kullanıma alma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,7 ve öncesinden oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açılır ve kopya tamamlandığında bir bildirim belirir.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin çözümler bölümünün ekran görüntüsü](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açılır.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16,7 ve önceki Takım Gezgini ' deki ' çözümler ve klasörler ' bildiriminin ekran görüntüsü](../get-started/media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, ' hiçbir çözüm bulunamadı ' iletisi görüntülenir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017&quot;

![Visual Studio giriş sayfası Takım Gezgini](media/team-explorer/team-explorer.png &quot;Visual Studio Takım Gezgini giriş sayfası.")

> [!TIP]
> Visual Studio açar ve **Takım Gezgini** görünmezse, menü çubuğundan **görünüm**  >  **Takım Gezgini** ' yı seçerek veya **ctrl** + **&#92;**, **ctrl** tuşuna basarak dosyayı açın + .

## <a name="connect-to-a-project-or-repository"></a>bir projeye veya depoya Bağlan

**Bağlan** sayfasındaki bir projeye veya depoya Bağlan.

![Takım Gezgini Bağlan sayfası](media/team-explorer/connect.png "Visual Studio Takım Gezgini Bağlan sayfası")

Bir projeye bağlanmak için:

1. **bağlantıları yönet** simgesini seçerek **Bağlan** sayfasını açın.

   ![Takım Gezgini bağlantıları yönetme düğmesi](media/team-explorer/manage-connections.png "Visual Studio ' de Takım Gezgini-bağlantıları Yönet düğmesi.")

1. **Bağlan** sayfasında,  > **bir projede bağlantıları Bağlan** yönet ' i seçin.

   ![Takım Gezgini bir projeye Bağlan](media/team-explorer/connect-project.png "Takım Gezgini-Visual Studio Project seçeneğine Bağlan.")

> [!TIP]
> Bir depodan bir proje açmak isterseniz, bkz. bir [depodan bir proje açma](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). yeni bir proje oluşturmak veya bir projeye kullanıcı eklemek istiyorsanız, bkz. [proje oluşturma (Azure DevOps)](/azure/devops/organizations/projects/create-project) ve [kullanıcıları projeye veya takıma ekleme (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Git ve Takım Gezgini yan yana karşılaştırın](git-team-explorer-feature-comparison.md)
- [Visual Studio yeni git deneyimi](git-with-visual-studio.md)
- [Takım Gezgini başvurusu](reference/team-explorer-reference.md)
- [bir projeye Bağlan (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Bir projeye bağlanma sorunlarını giderme](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
