---
title: Takım Gezgini başvurusu
description: Bir proje geliştirmek için işi Takım Gezgini ve diğer ekip üyeleriyle koordine olmak için bu çalışmalarda yer alan çeşitli işlevler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: bd336bb215e5631ef37955049ab7d2e94f169fa7a6ef73dc35d153ecbd143c9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387130"
---
# <a name="team-explorer-reference"></a>Takım Gezgini başvurusu

Bu makalede, Azure DevOps işlevleri hakkında daha fazla makaleye **Takım Gezgini.**

Bir **Takım Gezgini** geliştirmek ve size, takımınıza veya projelerinize atanan çalışmaları yönetmek için kod çalışmalarınızı diğer ekip üyeleriyle koordine etmek için Takım Gezgini araç penceresini kullanın. **Takım Gezgini** Git Visual Studio GitHub depolarına, Team Foundation sürüm denetimi (TFVC) depolarına ve [Azure DevOps Services'de](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi Azure DevOps Server'de (eski adıyla TFS) barındırılan [projelere](/azure/devops/index-all) bağlanır. Kaynak kodu, iş öğelerini ve derlemeleri yönetebilirsiniz.

## <a name="home-page"></a>Giriş sayfası

[Takım Gezgini'daki](../connect-team-project.md) bir **projeye bağlandikten** sonra, aşağıdaki bağlantılar Project **kullanılabilir** hale geldi:

- [Depoyu kopyalama](/azure/devops/repos/git/clone)
- [Web Portalı](/azure/devops/project/navigation/index)
- [Görev Panosu](/azure/devops/boards/sprints/task-board)

Giriş **sayfasında** git veya depolama [(TFVC)](/azure/devops/repos/tfvc/overview) [](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true) deposuna bağlı olup Team Foundation Sürüm Denetimi farklı işlevler vardır.

> [!TIP]
> İki sürüm denetim sistemi karşılaştırması için [bkz. Projeniz](/azure/devops/repos/tfvc/comparison-git-tfvc)için doğru sürüm Azure DevOps.

| Git **ile** giriş sayfası |  TFVC ile giriş sayfası |
| - | - |
| ![Takım Gezgini 2019'da Git ile Visual Studio sayfası](media/team-explorer-reference/team-explorer-git.png) | ![Takım Gezgini TFVC ile giriş Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Değişiklikler sayfası (Git)

Bkz. [İş işlemelerle kaydetme.](/azure/devops/repos/git/commits)

## <a name="branches-page-git"></a>Dallar sayfası (Git)

Bkz. [Dallarda iş oluşturma.](/azure/devops/repos/git/branches)

## <a name="pull-requests-page-git"></a>Çekme İstekleri sayfası (Git)

Bkz. [Çekme istekleriyle kodu gözden geçirme.](/azure/devops/repos/git/pullrequest)

## <a name="sync-page-git"></a>Eşitleme sayfası (Git)

Bkz. [Kodu getirme ve çekme ile güncelleştirme.](/azure/devops/repos/git/pulling)

## <a name="tags-page-git"></a>Etiketler sayfası (Git)

Bkz. [Git etiketleriyle çalışma.](/azure/devops/repos/git/git-tags)

## <a name="my-work-page-tfvc"></a>İş sayfam (TFVC)

Bkz. [Askıya alma/işi sürdürme ve](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) [Kod incelemesi.](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review)

## <a name="pending-changes-page-tfvc"></a>Bekleyen Değişiklikler sayfası (TFVC)

Bkz. [Bekleyen değişiklikleri yönetme,](/azure/devops/repos/tfvc/develop-code-manage-pending-changes) [Raf kümeleri bulma](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)ve [Çakışmaları çözümleme.](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts)

## <a name="source-control-explorer-page-tfvc"></a>Kaynak Denetim Gezgini sayfası (TFVC)

Bkz. [Dosya ve klasör ekleme/görüntüleme.](/azure/devops/repos/tfvc/add-files-server)

## <a name="work-items-page"></a>İş Öğeleri sayfası

İş **Öğeleri sayfası,** iş öğesi [sorgularını görmenizi](/azure/devops/boards/work-items/about-work-items) sağlar. Bkz.

- [İş öğeleri ekleme](/azure/devops/boards/backlogs/add-work-items)
- [Sorguları listele ve yönet için sorgu düzenleyicisini kullanma](/azure/devops/boards/queries/using-queries)
- [Sorgu klasörlerini düzenleme ve sorgu izinlerini ayarlama](/azure/devops/boards/queries/set-query-permissions)
- [Sorguyu Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Sorguyu Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Sorgu sonuçlarını kullanarak e-posta Outlook](/azure/devops/boards/queries/share-plans)
- [Sorgudan rapor oluşturma Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (yalnızca TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019'da yeni bir İş Öğeleri deneyimi var. [](/azure/devops/boards/work-items/set-work-item-experience-vs) 2019'da iş öğelerini görüntüleme Visual Studio için bkz. İş öğelerini [görüntüleme ve ekleme.](/azure/devops/boards/work-items/view-add-work-items)

::: moniker-end

## <a name="builds-page"></a>Derlemeler sayfası

Derlemeler **sayfası,** projenin derleme tanımlarını görmenizi sağlar.

Bkz.

- [Derleme işlem hatları oluşturma](/azure/devops/pipelines/tasks/index)
- [Derlemeleri görüntüleme ve yönetme](/azure/devops/pipelines/overview)
- [Derleme kuyruğu yönetme](/azure/devops/pipelines/agents/pools-queues)
- [Visual Studio için sürekli teslim (CD) araçlarını Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Uygulamanıza sürekli teslimi (CD) yapılandırma ve yürütme](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Ayarlar sayfası

Bu **Ayarlar,** bir proje veya proje koleksiyonu için yönetim özelliklerini yapılandırmaya olanak sağlar. Aşağıdaki makalelere bakın:

| Project | Project Koleksiyon | Diğer |
| - | - | - |
| [Güvenlik, Grup Üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Güvenlik, Kaynak Denetimi (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[İş Öğesi Alanları](/azure/devops/organizations/settings/set-area-paths)<br/>[İş Öğesi Yinelemeleri](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Portal Ayarlar](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Project Uyarı](/azure/devops/notifications/howto-manage-team-notifications) | [Güvenlik, Grup Üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kaynak Denetimi (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[İşlem Şablonu Yöneticisi](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git Genel Ayarlar](/azure/devops/repos/git/git-config)<br/>[Git Deposu Ayarlar](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Ayrıca bkz.

- [Ekip Gezgini'nde projelere bağlanma](../../ide/connect-team-project.md)