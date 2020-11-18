---
title: Takım Gezgini projelere bağlanma
description: Projeleri geliştirmek ve yönetmek için Visual Studio 'da Takım Gezgini kullanarak takım üyeleriyle nasıl çalışacağınızı öğrenin.
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 4e4fdfb26c601ce6b706c1c946ea9afe9b18ecb2
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850097"
---
# <a name="connect-to-projects-in-team-explorer"></a>Takım Gezgini projelere bağlanma

::: moniker range="vs-2017"

Bir proje geliştirmek ve size, takımınızı ya da projelerinize atanan işleri yönetmek için, **Takım Gezgini** araç penceresini diğer takım üyeleriyle koordine etmek için kullanın. **Takım Gezgini** , Visual Studio 'yu git ve GitHub depoları, Team Foundation sürüm denetimi (TFVC) depoları ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/index-all) (eski adıyla TFS) barındırılan projelere bağlar. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

**Takım Gezgini** araç penceresini, proje geliştirmek için kod çabalarınızı diğer takım üyeleriyle koordine etmek ve size, ekibinize veya projelerinize atanan işleri yönetmek için kullanabilirsiniz.

> [!IMPORTANT]
> Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes/)' nin son sürümüyle birlikte yeni git sürüm denetimi deneyimi artık varsayılan olarak açık durumdadır. Ancak Takım Gezgini kullanmaya devam etmeyi tercih ediyorsanız, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açın. Daha fazla bilgi için bkz. [Visual Studio 'Da git deneyimi](git-with-visual-studio.md) sayfası.

**Takım Gezgini** , Visual Studio 'yu git ve GitHub depoları, Team Foundation sürüm denetimi (TFVC) depoları ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/index-all) (eski adıyla TFS) barındırılan projelere bağlar. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

::: moniker-end

![Visual Studio 'da Takım Gezgini giriş sayfası](media/team-explorer/team-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 'yu açıp **Takım Gezgini** görünmezse, **View**  >  menü çubuğundan **Takım Gezgini** görüntüle ' yi seçerek veya **CTRL** + **&#92;**, **CTRL** tuşuna basarak dosyayı açın + **M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Bir projeye veya depoya bağlanma

**Bağlan** sayfasındaki bir projeye veya depoya bağlanın.

![Takım Gezgini sayfa bağlama](media/team-explorer/connect.png)

Bir projeye bağlanmak için:

1. **Bağlantıları Yönet** simgesini seçerek **Bağlan** sayfasını açın.

   ![Takım Gezgini bağlantıları yönetme düğmesi](media/team-explorer/manage-connections.png)

1. **Bağlan** sayfasında **Bağlantıları Yönet**' i seçin  >  **bir projeye bağlanın**.

   ![Takım Gezgini bir projeye bağlanma](media/team-explorer/connect-project.png)

> [!TIP]
> Bir depodan bir proje açmak isterseniz, bkz. bir [depodan bir proje açma](../get-started/tutorial-open-project-from-repo.md). Yeni bir proje oluşturmak veya bir projeye Kullanıcı eklemek istiyorsanız, bkz. [Proje oluşturma (Azure DevOps)](/azure/devops/organizations/projects/create-project) ve [bir projeye veya takıma Kullanıcı ekleme (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da yeni git deneyimi](git-with-visual-studio.md)
- [Öğretici: bir depodan bir proje açın](../get-started/tutorial-open-project-from-repo.md)
- [Takım Gezgini başvurusu](reference/team-explorer-reference.md)
- [Bir projeye bağlanma (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Bir projeye bağlanma sorunlarını giderme](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
