---
title: Bir çözümde proje yüklemeyi yönetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702726"
---
# <a name="manage-project-loading-in-a-solution"></a>Bir çözümde proje yüklemeyi yönetme
Visual Studio çözümleri, çok sayıda proje içerebilir. Varsayılan Visual Studio davranışı, çözüm açıldığı sırada bir Çözümdeki tüm projeleri yüklemek ve tümünün yüklemeyi bitirene kadar herhangi bir projede erişime izin vermek değildir. Proje yükleme işleminin süresi iki dakikadan uzun sürer, yüklenen proje sayısını ve toplam proje sayısını gösteren bir ilerleme çubuğu görüntülenir. Kullanıcı birden çok projeyle oluşan bir çözümde çalışırken projeleri kaldırabilirler, ancak bu yordamın bazı dezavantajları vardır: kaldırılan projeler, yeniden derleme çözümünün bir parçası olarak derlenmez ve kapalı projelerin türlerin ve üyelerinin IntelliSense açıklamaları gösterilmez.

 Geliştiriciler bir çözüm yük Yöneticisi oluşturarak çözüm yükleme sürelerini azaltabilir ve proje yükleme davranışını yönetebilir. Çözüm yükleme yöneticisi, bir arka plan derlemesi başlatmadan önce projelerin yüklenmesini, diğer arka plan görevleri tamamlanana kadar Gecikmeli yüklemeyi geciktirmesini ve diğer proje yük yönetimi görevlerini gerçekleştirmenizi sağlayabilir.

## <a name="create-a-solution-load-manager"></a>Çözüm Yükleme Yöneticisi oluşturma
 Geliştiriciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> , çözüm yük yöneticisinin etkin olduğu Visual Studio 'yu uygulayarak ve inceleyerek çözüm yükleme yöneticisi oluşturabilir.

### <a name="activate-a-solution-load-manager"></a>Çözüm yükleme yöneticisini etkinleştirme
 Visual Studio, belirli bir zamanda yalnızca bir çözüm yük yöneticisine izin veriyor, bu nedenle çözüm yükleme yöneticisini etkinleştirmek istediğinizde Visual Studio 'Yu uygulamalısınız. İkinci bir çözüm yükleme yöneticisi daha sonra etkinleştirilirse, çözüm yükleme yöneticinizin bağlantısı kesilir.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>Hizmeti almanız ve __VSPROPID4 ayarlamanız gerekir [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Yöntemi, Visual Studio kapatılırken veya __VSPROPID4 ile çağırarak etkin çözüm yük Yöneticisi olarak farklı bir paket çekilirken çağrılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Farklı türlerde çözüm Yükleme Yöneticisi stratejileri
 Yönetmek istediği çözüm türlerine bağlı olarak çözüm yükleme yöneticilerini farklı yollarla uygulayabilirsiniz.

 Çözüm yükleme yöneticisi çözüm yüklemeyi genel olarak yönetgeliyorsa, VSPackage 'un bir parçası olarak uygulanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Bir değeri Ile VSPackage 'a eklenerek, paket, tekrar yükleme olarak ayarlanmalıdır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Çözüm yükleme yöneticisi daha sonra <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yönteminde etkinleştirilebilir.

> [!NOTE]
> Paketleri oto yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).

 Visual Studio yalnızca son çözüm yük yöneticisini etkinleştirecek şekilde tanıdığından, genel çözüm yükleme yöneticileri kendilerini etkinleştirmeden önce mevcut bir yük Yöneticisi olup olmadığını her zaman saptamalıdır. `GetProperty()`__VSPROPID4 için çözüm hizmetinde çağırma yapıyorsanız [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null` , etkin çözüm yükleme yöneticisi yok. Null döndürmezse, nesnenin çözüm yükleme yöneticisiyle aynı olup olmadığını kontrol edin.

 Çözüm Load Manager, yalnızca birkaç tür çözümü yönetecekseniz, VSPackage çözüm yükleme olaylarına abone olabilir (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> çözüm yükleme yöneticisini etkinleştirmek için olay işleyicisini kullanabilirsiniz.

 Çözüm Yükleme Yöneticisi yalnızca belirli çözümleri yönetmek için gerekliyse, etkinleştirme bilgileri çözüm dosyasının bir parçası olarak kalıcı hale getirilir ve çözüm çözümü için bu bölümü çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> .

 Belirli çözüm yükü yöneticileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> , diğer çözüm yükü yöneticileriyle çakışmayacak şekilde olay işleyicisinde kendilerini devre dışı bırakmalıdır.

 Yalnızca genel proje yükleme özelliklerini sürdürmek için bir çözüm yük yöneticisine ihtiyacınız varsa (örneğin, Seçenekler sayfasında ayarlanan özellikler), çözüm yükleme Yöneticisini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> olay işleyicisinde etkinleştirebilir, ayarı çözüm özelliklerinde kalıcı hale getirebilirsiniz, sonra çözüm yükleme yöneticisini devre dışı bırakabilirsiniz.

## <a name="handle-solution-load-events"></a>Çözüm yükleme olaylarını işle
 Çözüm yükleme olaylarına abone olmak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> çözüm yükleme yöneticisini etkinleştirdiğinizde çağırın. Uygulamasını uygularsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , farklı proje yükleme özellikleriyle ilgili olaylara yanıt verebilirsiniz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bu olay bir çözüm açılmadan önce tetiklenir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Bu olay çözüm tamamen yüklendikten sonra, ancak arka plan projesi yüklemesi yeniden başlamadan önce tetiklenir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Bu olay, bir çözüm yükleme yöneticisi olup olmadığına bakılmaksızın, bir çözüm başlangıçta tamamen yüklendikten sonra tetiklenir. Ayrıca, çözüm tam olarak yüklendiğinde arka plan yükleme veya talep yükleme sonrasında da tetiklenir. Aynı zamanda yeniden <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> etkinleştirilir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bu olay bir proje (veya projeleri) yüklenmeden önce tetiklenir. Projeler yüklenmeden önce diğer arka plan işlemlerinin tamamlandığından emin olmak için, `pfShouldDelayLoadToNextIdle` **true**olarak ayarlayın.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Bu olay bir proje toplu işi yüklenirken tetiklenir. `fIsBackgroundIdleBatch`True ise, projeler arka planda yüklenir; `fIsBackgroundIdleBatch` yanlışsa, bir Kullanıcı isteği sonucunda projeler zaman uyumlu olarak yüklenir; Örneğin, Kullanıcı Çözüm Gezgini bekleyen bir projeyi genişlediğinde. Bu olayı, aksi takdirde ' de gerçekleştirilmesi gereken pahalı bir iş yapmak için işleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Bu olay, bir Batch projesi yüklendikten sonra harekete geçirilir.

## <a name="detect-and-manage-solution-and-project-loading"></a>Çözüm ve proje yüklemeyi Algıla ve Yönet
 Projelerin ve çözümlerin yüklenme durumunu algılamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> aşağıdaki değerlerle çağırın:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` `true` çözüm ve tüm projeleri yüklüyse, aksi takdirde ' i döndürür `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` `true` bir proje toplu işleminin şu anda arka planda yüklenmekte olup olmadığını döndürür, aksi takdirde `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` bir `true` Proje toplu işi şu anda bir Kullanıcı komutunun veya başka bir açık yükün sonucu olarak zaman uyumlu olarak yükleniyorsa, aksi takdirde döndürür `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` `true` çözüm şu anda kapalıysa döndürür, aksi takdirde `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` `true` bir çözümün açık durumda olup olmadığını döndürür, aksi takdirde `false` .

Ayrıca, aşağıdaki yöntemlerden birini çağırarak projelerin ve çözümlerin yüklendiğinden emin olabilirsiniz:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: Bu yöntemi çağırmak, bir çözümdeki projeleri Yöntem dönüşünden önce yüklenecek şekilde zorlar.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: Bu yöntemi çağırmak, içindeki projeleri `guidProject` Yöntem dönüşden önce yüklemeye zorlar.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: Bu yöntemi çağırmak, öğesini `guidProjectID` metot dönüşden önce yüklemeye zorlar.
