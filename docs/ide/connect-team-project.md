---
title: Ekip Gezgini'nde projelere bağlanma
description: Proje geliştirme ve yönetme Takım Gezgini ekip Visual Studio çalışmak için bu iş birli çalışmalarında nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: <=vs-2019
ms.openlocfilehash: b45399f7a4115ce5946a67caca22ca92148e7434
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308252"
---
# <a name="connect-to-projects-in-team-explorer"></a>Ekip Gezgini'nde projelere bağlanma

::: moniker range="vs-2017"

Bir **Takım Gezgini** geliştirme ve size, takımınıza veya projelerinize atanan çalışmaları yönetmek için kod çalışmalarınızı diğer ekip üyeleriyle koordine etmek için Takım Gezgini araç penceresini kullanın. **Takım Gezgini** Git Visual Studio GitHub depolarına, Team Foundation sürüm denetimi (TFVC) depolarına ve [Azure DevOps Services'de](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi Azure DevOps Server'de (eski adıyla TFS) barındırılan [projelere](/azure/devops/index-all) bağlanır. Kaynak kodu, iş öğelerini ve derlemeleri yönetebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

Takım Gezgini, Visual Studio Team Foundation sürüm denetimi (TFVC) depolarına ve [Azure DevOps Services'de](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi Azure DevOps Server 'de (eski adıyla TFS) barındırılan [projelere](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) bağlanır. Kaynak kodu, iş öğelerini ve derlemeleri yönetebilirsiniz.

> [!IMPORTANT]
> Visual Studio 2019 [**sürüm 16.8**](/visualstudio/releases/2019/release-notes-history)sürümünde Git sürüm denetimi deneyimi varsayılan olarak açıktır. Bunun git ve Takım Gezgini karşılaştırması hakkında daha fazla bilgi edinmek için [**Bkz. Git**](../version-control/git-team-explorer-feature-comparison.md) ve Takım Gezgini karşılaştırması.
>
> Ancak, Takım Gezgini kullanmaya devam etmek isterseniz, Araçlar  Seçenekler Ortam Önizleme Özellikleri'ne gidin ve Yeni Git kullanıcı deneyimi >  >  >  **onay** kutusunu açıp temizleyin.

Bir Takım Gezgini bağlanmak için Visual Studio 2019 sürümüne bağlıdır.

## <a name="in-version-168-and-later"></a>Sürüm 16.8 ve sonraki sürümlerde

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

## <a name="in-version-167-and-earlier"></a>Sürüm 16.7 ve önceki sürümlerde

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde yer alan 'Depoya göz atma Azure DevOps' bölümünün yer Visual Studio' penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Projeye Bağlan iletişim kutusunda,** bağlanmak istediğiniz bir repo seçin ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerden oluşturulan 'Projeye Bağlan' iletişim kutusunun ekran görüntüsü](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

   Visual Studio, **Takım Gezgini** tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki bir sürümde yer alan Takım Gezgini penceresinin ekran görüntüsü](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için Klasör Görünümünü **Göster bağlantısını** seçin.

     ![Takım Gezgini 2019 sürüm 16.7 ve önceki sürümlerindeki Visual Studio penceresinin Çözümler bölümünün ekran görüntüsü](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **,** Çözüm Gezgini.

1. Açılacak **bir çözüm dosyası** (özel olarak bir .sln dosyası) aramak için Çözümler ve Klasörler bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Takım Gezgini 'Çözümler ve Klasörler' bildiriminin ekran görüntüsü](../get-started/media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyanız yoksa bir 'Çözüm Bulunamadı' iletisi görüntülenir. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017&quot;

![Takım Gezgini Giriş sayfası Visual Studio](media/team-explorer/team-explorer.png &quot;Takım Gezgini - Giriş sayfası Visual Studio.")

> [!TIP]
> Visual Studio ve **Takım Gezgini** görünmüyorsa, menü çubuğundan Görünüm Takım Gezgini'i seçerek veya  >   **Ctrl** +&#92;, **Ctrl** M **tuşlarına** basarak + **açın.**

## <a name="connect-to-a-project-or-repository"></a>Projeye veya depoya bağlanma

Bağlan sayfasında bir projeye veya **depoya** bağlanabilirsiniz.

![Takım Gezgini'de bağlantı sayfası](media/team-explorer/connect.png "Takım Gezgini - Bağlan sayfası Visual Studio")

Bir projeye bağlanmak için:

1. Bağlantıları **Yönet simgesini** seçerek **Bağlan sayfasını** açın.

   ![Takım Gezgini'de Bağlantıları Yönet düğmesi](media/team-explorer/manage-connections.png "Takım Gezgini - Bağlantıları Yönet düğmesi Visual Studio.")

1. Bağlan **sayfasında,** Bağlantıları Yönet **Projeye** > **bağlan'ı seçin.**

   ![Takım Gezgini'da bir projeye bağlanma](media/team-explorer/connect-project.png "Takım Gezgini - Bir Proje seçeneğine bağlan seçeneği Visual Studio.")

> [!TIP]
> Bir repodan proje açmak için bkz. [Bir repodan proje açma.](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) Yeni bir proje oluşturmak veya bir projeye kullanıcı eklemek için bkz. Proje [oluşturma (Azure DevOps)](/azure/devops/organizations/projects/create-project) ve Bir projeye veya takıma kullanıcı ekleme [(Azure DevOps).](/azure/devops/organizations/security/add-users-team-project)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Git ile Takım Gezgini yan yana karşılaştırma](git-team-explorer-feature-comparison.md)
- [Visual Studio'daki yeni Git deneyimi](git-with-visual-studio.md)
- [Takım Gezgini başvurusu](reference/team-explorer-reference.md)
- [Projeye bağlanma (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Projeye bağlanma sorunlarını giderme](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
