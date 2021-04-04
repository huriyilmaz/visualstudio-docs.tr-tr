---
title: Ekip Gezgini'nde projelere bağlanma
description: Projeleri geliştirmek ve yönetmek için Visual Studio 'da Takım Gezgini kullanarak takım üyeleriyle nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/31/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 78a71911bb4334e04a085d91ff51238d34981beb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216611"
---
# <a name="connect-to-projects-in-team-explorer"></a>Ekip Gezgini'nde projelere bağlanma

::: moniker range="vs-2017"

Bir proje geliştirmek ve size, takımınızı ya da projelerinize atanan işleri yönetmek için, **Takım Gezgini** araç penceresini diğer takım üyeleriyle koordine etmek için kullanın. **Takım Gezgini** , Visual Studio 'yu git ve GitHub depoları, Team Foundation sürüm denetimi (TFVC) depoları ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/index-all) (eski adıyla TFS) barındırılan projelere bağlar. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

Takım Gezgini, Visual Studio 'Yu Team Foundation sürüm denetimi (TFVC) depolarına ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) barındırılan projelere (eski adıyla TFS) bağlar. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

> [!IMPORTANT]
> Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes/)' nin son sürümüyle birlikte yeni git sürüm denetimi deneyimi artık varsayılan olarak açık durumdadır. Takım Gezgini ile nasıl Karşılaştırıldığı hakkında daha fazla bilgi edinmek istiyorsanız [**Git ve Takım Gezgini sayfasının yan yana karşılaştırmasını**](git-team-explorer-feature-comparison.md) inceleyin.
>
> Ancak Takım Gezgini kullanmaya devam etmeyi tercih ediyorsanız, **Araçlar** > **Seçenekler** > **ortam** > **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açın.

Bir projeye bağlanmak için Takım Gezgini kullandığınızda, kullanmakta olduğunuz Visual Studio 2019 sürümüne bağlıdır.

## <a name="in-version-168-and-later"></a>Sürüm 16,8 ve üzeri sürümlerde

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

## <a name="in-version-167-and-earlier"></a>Sürüm 16,7 ve önceki sürümlerde

1. Visual Studio 2019 ' i açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluşturma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya Gözatatıon** bölümünde **Azure DevOps**' u seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Azure DevOps 'u listeleyen ' bir depoya göz at ' bölümü ile ' kopya veya kullanıma alma ' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,7 ve öncesinde oluşturulan ' projeye Bağlan ' iletişim kutusunun ekran görüntüsü](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişiminiz olan Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açar ve kopya tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![Kopyalama tamamlandıktan sonra Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin çözümler bölümünün ekran görüntüsü](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açar.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini ' çözümler ve klasörler ' bildiriminin ekran görüntüsü](../get-started/media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, ' hiçbir çözüm bulunamadı ' iletisi görüntülenir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

![Visual Studio 'da Takım Gezgini giriş sayfası](media/team-explorer/team-explorer.png "Visual Studio 'daki Takım Gezgini giriş sayfası.")

> [!TIP]
> Visual Studio 'yu açıp **Takım Gezgini** görünmezse,   >  menü çubuğundan **Takım Gezgini** görüntüle ' yi seçerek veya **CTRL** + **&#92;**, **CTRL** tuşuna basarak dosyayı açın + .

## <a name="connect-to-a-project-or-repository"></a>Bir projeye veya depoya bağlanma

**Bağlan** sayfasındaki bir projeye veya depoya bağlanın.

![Takım Gezgini sayfa bağlama](media/team-explorer/connect.png "Visual Studio 'da Takım Gezgini-Connect sayfası")

Bir projeye bağlanmak için:

1. **Bağlantıları Yönet** simgesini seçerek **Bağlan** sayfasını açın.

   ![Takım Gezgini bağlantıları yönetme düğmesi](media/team-explorer/manage-connections.png "Visual Studio 'da Takım Gezgini-bağlantıları Yönet düğmesi.")

1. **Bağlan** sayfasında **Bağlantıları Yönet** ' i seçin > **bir projeye bağlanın**.

   ![Takım Gezgini bir projeye bağlanma](media/team-explorer/connect-project.png "Takım Gezgini-Visual Studio 'da bir proje seçeneğine bağlanın.")

> [!TIP]
> Bir depodan bir proje açmak isterseniz, bkz. bir [depodan bir proje açma](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Yeni bir proje oluşturmak veya bir projeye Kullanıcı eklemek istiyorsanız, bkz. [Proje oluşturma (Azure DevOps)](/azure/devops/organizations/projects/create-project) ve [bir projeye veya takıma Kullanıcı ekleme (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Git ve Takım Gezgini yan yana karşılaştırın](git-team-explorer-feature-comparison.md)
- [Visual Studio 'da yeni git deneyimi](git-with-visual-studio.md)
- [Takım Gezgini başvurusu](reference/team-explorer-reference.md)
- [Bir projeye bağlanma (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Bir projeye bağlanma sorunlarını giderme](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
