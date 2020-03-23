---
title: Takım Gezgini başvurusu
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74538570"
---
# <a name="team-explorer-reference"></a>Takım Gezgini başvurusu

Bu makalede, **Team Explorer'daki**çeşitli işlevler hakkında Azure DevOps makalelerine bağlantılar sağlanmaktadır.

Bir proje geliştirmek ve size, ekibinize veya projelerinize atanan işleri yönetmek için kod çabalarınızı diğer ekip üyeleriyle koordine etmek için **Takım Gezgini** aracı penceresini kullanın. **Team Explorer,** Visual Studio'yu Git ve GitHub depolarına, Team Foundation sürüm denetimine (TFVC) ve [Azure DevOps Hizmetleri'nde](/azure/devops/user-guide/what-is-azure-devops-services) veya şirket içi Azure [DevOps Server'da](/azure/devops/index-all) (eski adıyla TFS olarak da bilinir) barındırılan projelere bağlar. Kaynak kodu, iş öğeleri ve yapılar yönetebilirsiniz.

## <a name="home-page"></a>Giriş sayfası

**Team Explorer'daki** [bir projeye bağlandıktan](../connect-team-project.md) sonra **Proje** bölümünde aşağıdaki bağlantılar kullanılabilir hale gelir:

- [Klon deposu](/azure/devops/repos/git/clone)
- [Web Portalı](/azure/devops/project/navigation/index)
- [Görev Panosu](/azure/devops/boards/sprints/task-board)

**Giriş** sayfası, bir [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) veya Team Foundation Sürüm [Denetimi (TFVC)](/azure/devops/repos/tfvc/overview) deposuna bağlı olup olmadığınıza bağlı olarak farklı işlevlere sahiptir.

> [!TIP]
> İki sürüm kontrol sisteminin karşılaştırılması [için](/azure/devops/repos/tfvc/comparison-git-tfvc)bkz.

| Git ile **ana** sayfa | TFVC ile **giriş** sayfası |
| - | - |
| ![Visual Studio 2019'da Git ile Takım Gezgini Giriş sayfası](media/team-explorer-reference/team-explorer-git.png) | ![Visual Studio'da TFVC ile Takım Gezgini Giriş sayfası](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Sayfayı değiştirir (Git)

Bkz. [Commits ile çalışmayı kaydet.](/azure/devops/repos/git/commits)

## <a name="branches-page-git"></a>Şubeler sayfası (Git)

Bkz. [Dallarda iş oluşturma.](/azure/devops/repos/git/branches)

## <a name="pull-requests-page-git"></a>İstekleri Çekme sayfası (Git)

[Çekme istekleriiçeren Gözden Geçirme koduna](/azure/devops/repos/git/pullrequest)bakın.

## <a name="sync-page-git"></a>Eşitleme sayfası (Git)

Bkz. [Getir ve çek ile kodu güncelleştir.](/azure/devops/repos/git/pulling)

## <a name="tags-page-git"></a>Etiketler sayfası (Git)

[Git etiketleri ile Çalışma'ya](/azure/devops/repos/git/git-tags)bakın.

## <a name="my-work-page-tfvc"></a>Çalışma sayfam (TFVC)

Bkz. [Askıya Alma/devam çalışması](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) ve [Kod incelemesi.](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review)

## <a name="pending-changes-page-tfvc"></a>Bekleyen Değişiklikler sayfası (TFVC)

Bkz. [Bekleyen değişiklikleri yönet,](/azure/devops/repos/tfvc/develop-code-manage-pending-changes) [raf kümelerini bul](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)ve [çakışmaları çöz.](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts)

## <a name="source-control-explorer-page-tfvc"></a>Kaynak Denetim Explorer sayfası (TFVC)

Bkz. [Dosya ve klasörleri ekle/görüntüleme.](/azure/devops/repos/tfvc/add-files-server)

## <a name="work-items-page"></a>Çalışma Öğeleri sayfası

**Çalışma Öğeleri** sayfası [iş öğesi](/azure/devops/boards/work-items/about-work-items) sorgularını görmenizi sağlar. Bkz.

- [İş öğeleri ekleme](/azure/devops/boards/backlogs/add-work-items)
- [Sorguları listelemek ve yönetmek için sorgu düzenleyicisini kullanın](/azure/devops/boards/queries/using-queries)
- [Sorgu klasörlerini düzenleme ve sorgu izinlerini ayarlama](/azure/devops/boards/queries/set-query-permissions)
- [Excel'de sorguaç](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Project'te sorguaç](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Outlook'u kullanarak e-posta sorgusu sonuç listesi](/azure/devops/boards/queries/share-plans)
- [Excel'de sorgudan rapor oluşturma](/azure/devops/report/excel/create-status-and-trend-excel-reports) (yalnızca TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019'da yeni bir [İş Öğeleri deneyimi](/azure/devops/boards/work-items/set-work-item-experience-vs) var. Visual Studio 2019'da iş öğelerini görüntüleme hakkında daha fazla bilgi için [Görünüm'e](/azure/devops/boards/work-items/view-add-work-items)bakın ve iş öğeleri ekleyin.

::: moniker-end

## <a name="builds-page"></a>Sayfa oluşturur

**Yapılar** sayfası, proje için yapı tanımlarını görmenizi sağlar.

Bkz.

- [Yapı ardışık hatları oluşturma](/azure/devops/pipelines/tasks/index)
- [Yapıları görüntüleme ve yönetme](/azure/devops/pipelines/overview)
- [Yapı sırasını yönetme](/azure/devops/pipelines/agents/pools-queues)
- [Visual Studio için sürekli teslimat (CD) araçlarını yükleyin](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Uygulamanız için sürekli teslimatı (CD) yapılandırın ve çalıştırın](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Ayarlar sayfası

**Ayarlar** sayfası, proje veya proje koleksiyonu için yönetim özelliklerini yapılandırmanıza olanak tanır. Aşağıdaki makalelere bakın:

| Project | Proje Koleksiyonu | Diğer |
| - | - | - |
| [Güvenlik, Grup Üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Güvenlik, Kaynak Kontrol (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[İş Öğesi Alanları](/azure/devops/organizations/settings/set-area-paths)<br/>[Çalışma Öğesi Yinelemeleri](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Portal Ayarları](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Proje Uyarıları](/azure/devops/notifications/howto-manage-team-notifications) | [Güvenlik, Grup Üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kaynak Denetimi (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[İşlem Şablon Yöneticisi](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Genel Ayarları Git](/azure/devops/repos/git/git-config)<br/>[Git Deposu Ayarları](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Ayrıca bkz.

- [Team Explorer'daki projelere bağlanma](../../ide/connect-team-project.md)