---
title: Takım Gezgini başvurusu
description: İşi yönetmek için Takım Gezgini çeşitli işlevler hakkında bilgi edinin ve proje geliştirmek için diğer takım üyeleriyle koordine edin.
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jmartens
ms.openlocfilehash: 85d007ae7aec5bb56b85e4b1861845f81687dd68
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785877"
---
# <a name="team-explorer-reference"></a>Takım Gezgini başvurusu

bu makalede, **Takım Gezgini** çeşitli işlevlerle ilgili Azure DevOps makalelerin bağlantıları sağlanmaktadır.

Bir proje geliştirmek ve size, takımınızı ya da projelerinize atanan işleri yönetmek için, **Takım Gezgini** araç penceresini diğer takım üyeleriyle koordine etmek için kullanın. **Takım Gezgini** Visual Studio Git ve GitHub depolara, Team Foundation sürüm denetimi (tfvc) depolarına ve [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi [Azure DevOps Server](/azure/devops/index-all) (eski adıyla TFS) barındırılan projelere bağlanır. Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

## <a name="home-page"></a>Giriş sayfası

**Takım Gezgini** [bir projeye](../connect-team-project.md) bağlandıktan sonra, **Project** bölümünde aşağıdaki bağlantılar kullanılabilir hale gelir:

- [Depoyu Kopyala](/azure/devops/repos/git/clone)
- [Web portalı](/azure/devops/project/navigation/index)
- [Görev panosu](/azure/devops/boards/sprints/task-board)

**giriş** sayfası, bir [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true) veya [Team Foundation Sürüm Denetimi (tfvc)](/azure/devops/repos/tfvc/overview) deposuna bağlı olmanıza bağlı olarak farklı işlevlere sahiptir.

> [!TIP]
> İki sürüm denetim sisteminin karşılaştırması için bkz. [projeniz için doğru sürüm denetimini seçme (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| Git ile **ana** sayfa | TFVC ile **ana** sayfa |
| - | - |
| ![Git ile giriş sayfası Takım Gezgini Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![TFVC ile ana sayfa Takım Gezgini Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Değişiklikler sayfası (git)

Bkz. [yürütmelerle Iş kaydetme](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Dallar sayfası (git)

Bkz. [dallarda Iş oluşturma](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Çekme Istekleri sayfası (git)

Bkz. [çekme istekleri ile kodu gözden geçirme](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Eşitleme sayfası (git)

Bkz. [Fetch ve pull Ile güncelleştirme kodu](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Etiketler sayfası (git)

Bkz. [Git etiketleriyle çalışma](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Çalışma sayfam (TFVC)

Bkz. [askıya alma/sürdürülme](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) ve [Kod İnceleme](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Bekleyen değişiklikler sayfası (TFVC)

Bkz. [bekleyen değişiklikleri yönetme](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [raf kümeleri bulma](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)ve [çakışmaları çözme](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Kaynak Denetim Gezgini sayfası (TFVC)

Bkz. [dosya ve klasör ekleme/görüntüleme](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>İş öğeleri sayfası

**Iş öğeleri** sayfası, [çalışma öğesi](/azure/devops/boards/work-items/about-work-items) sorgularını görmenizi sağlar. Bkz.

- [İş öğeleri ekle](/azure/devops/boards/backlogs/add-work-items)
- [Sorguları listelemek ve yönetmek için sorgu düzenleyicisini kullanma](/azure/devops/boards/queries/using-queries)
- [Sorgu klasörlerini düzenleme ve sorgu izinlerini ayarlama](/azure/devops/boards/queries/set-query-permissions)
- [Sorguyu Excel aç](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Sorguyu Project aç](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Outlook kullanarak e-posta sorgu sonuçları listesi](/azure/devops/boards/queries/share-plans)
- [Excel sorgudan rapor oluşturma](/azure/devops/report/excel/create-status-and-trend-excel-reports) (yalnızca TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019 ' de yeni bir [iş öğeleri deneyimi](/azure/devops/boards/work-items/set-work-item-experience-vs) var. Visual Studio 2019 ' de iş öğelerini görüntüleme hakkında daha fazla bilgi için bkz. [çalışma öğelerini görüntüleme ve ekleme](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Yapılar sayfası

**Yapılar** sayfası, proje için yapı tanımlarını görmenizi sağlar.

Bkz.

- [Derleme işlem hatları oluşturma](/azure/devops/pipelines/tasks/index)
- [Yapıları görüntüleme ve yönetme](/azure/devops/pipelines/overview)
- [Derleme kuyruğunu yönetme](/azure/devops/pipelines/agents/pools-queues)
- [Visual Studio için sürekli teslim (CD) araçları 'nı yükler](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Uygulamanız için sürekli teslimi (CD) yapılandırma ve yürütme](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Ayarlar sayfası

**Ayarlar** sayfası, bir proje ya da proje koleksiyonu için yönetim özelliklerini yapılandırmanıza olanak tanır. Aşağıdaki makalelere bakın:

| Project | Project Koleksiyon | Diğer |
| - | - | - |
| [Güvenlik, Grup üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Güvenlik, kaynak denetimi (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Çalışma öğesi alanı](/azure/devops/organizations/settings/set-area-paths)<br/>[Çalışma öğesi yinelemeleri](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Portal Ayarlar](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Project Larınız](/azure/devops/notifications/howto-manage-team-notifications) | [Güvenlik, Grup üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kaynak denetimi (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[İşlem şablonu Yöneticisi](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git genel Ayarlar](/azure/devops/repos/git/git-config)<br/>[Git deposu Ayarlar](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Ayrıca bkz.

- [Ekip Gezgini'nde projelere bağlanma](../../ide/connect-team-project.md)