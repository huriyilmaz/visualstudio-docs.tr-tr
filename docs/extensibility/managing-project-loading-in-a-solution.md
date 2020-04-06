---
title: Çözümde Proje Yüklemeyi Yönetme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702726"
---
# <a name="manage-project-loading-in-a-solution"></a>Bir çözümde proje yüklemeyi yönetme
Visual Studio çözümleri çok sayıda proje içerebilir. Varsayılan Visual Studio davranışı, çözüm açıldığında tüm projeleri bir çözüme yüklemek ve tüm yüklemeyi bitirene kadar kullanıcının projelerden herhangi birini erişmesine izin vermemektir. Proje yükleme işlemi iki dakikadan fazla sürecekse, yüklenen proje sayısını ve toplam proje sayısını gösteren bir ilerleme çubuğu görüntülenir. Kullanıcı birden çok projeyle bir çözümde çalışırken projeleri boşaltabilir, ancak bu yordamın bazı dezavantajları vardır: boşaltılan projeler Yeniden Oluşturma Çözümü komutunun bir parçası olarak oluşturulmaz ve kapalı projelerin türlerinin ve üyelerinin IntelliSense açıklamaları görüntülenmez.

 Geliştiriciler, bir çözüm yük yöneticisi oluşturarak çözüm yükleme sürelerini azaltabilir ve proje yükleme davranışını yönetebilir. Çözüm yük yöneticisi, arka plan oluşturmayı başlatmadan önce projelerin yüklendiğinden emin olabilir, diğer arka plan görevleri tamamlanana kadar arka plan yüklemesini geciktirebilir ve diğer proje yük yönetimi görevlerini gerçekleştirebilir.

## <a name="create-a-solution-load-manager"></a>Çözüm yük yöneticisi oluşturma
 Geliştiriciler Visual Studio'ya çözüm <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> yük yöneticisinin etkin olduğunu uygulayarak ve tavsiye ederek bir çözüm yük yöneticisi oluşturabilirler.

### <a name="activate-a-solution-load-manager"></a>Çözüm yük yöneticisini etkinleştirme
 Visual Studio belirli bir zamanda yalnızca bir çözüm yük yöneticisine izin verir, bu nedenle çözüm yük yöneticinizi etkinleştirmek istediğinizde Visual Studio'ya tavsiyede bulunmalısınız. Daha sonra ikinci bir çözüm yük yöneticisi etkinleştirilirse, çözüm yük yöneticinizin bağlantısı kesilir.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> Hizmeti almalı ve [__VSPROPID4 ayarlamalısınız. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> yöntem, Visual Studio kapatıldığında veya __VSPROPID4 arayarak etkin çözüm yük yöneticisi olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> farklı bir paket devraldığında çağrılır. [ VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Farklı türde çözüm yük yöneticisi için stratejiler
 Çözüm yük yöneticilerini, yönetmeleri gereken çözüm türlerine bağlı olarak farklı şekillerde uygulayabilirsiniz.

 Çözüm yük yöneticisi genel olarak çözüm yüklemesini yönetmek için yapılmışsa, bir VSPackage'ın parçası olarak uygulanabilir. Paket, VSPackage'a değeri olan <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> paket eklenerek otomatik <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>olarak yüklenmeye ayarlanmalıdır. Çözüm yük yöneticisi daha sonra <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemde etkinleştirilebilir.

> [!NOTE]
> Otomatik yükleme paketleri hakkında daha fazla bilgi için [Yükleme VSPackages'e](../extensibility/loading-vspackages.md)bakın.

 Visual Studio etkinleştirilecek yalnızca son çözüm yük yöneticisini tanıdığından, genel çözüm yük yöneticileri kendilerini etkinleştirmeden önce her zaman varolan bir yük yöneticisi olup olmadığını tespit etmelidir. Çözüm `GetProperty()` hizmetini __VSPROPID4 için [çağırıyorsanız. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`döndürür, etkin çözüm yük yöneticisi yoktur. Null döndürmezse, nesnenin çözüm yük yöneticinizle aynı olup olmadığını kontrol edin.

 Çözüm yük yöneticisi yalnızca birkaç tür çözümü yönetmek için yapılmışsa, VSPackage çözüm <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>yükleme olaylarına abone olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> (arayarak), ve çözüm yük yöneticisini etkinleştirmek için olay işleyicisini kullanabilir.

 Çözüm yük yöneticisi yalnızca belirli çözümleri yönetmek için direnilirse, etkinleştirme bilgileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> çözüm öncesi bölümü arayarak çözüm dosyasının bir parçası olarak kalıcı hale alınabilir.

 Belirli çözüm yük yöneticileri, diğer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> çözüm yük yöneticileriyle çakışmamak için olay işleyicisinde kendilerini devre dışı bırakmalıdır.

 Yalnızca genel proje yük özelliklerini (örneğin, Seçenekler sayfasında ayarlanan özellikler) sürdürmek için bir çözüm yük <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> yöneticisine ihtiyacınız varsa, olay işleyicisindeki çözüm yük yöneticisini etkinleştirebilir, çözüm özelliklerindeki ayarı devam ettirebilirsiniz ve çözüm yük yöneticisini devre dışı bırakabilirsiniz.

## <a name="handle-solution-load-events"></a>Çözüm yük olaylarını işleme
 Çözüm yükleme olaylarına abone <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> olmak için, çözüm yük yöneticinizi etkinleştirdiğinizde arayın. Uygularsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>farklı proje yükleme özellikleriyle ilgili olaylara yanıt verebilirsiniz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bu olay, çözüm açılmadan önce ateşlenir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Bu olay, çözüm tamamen yüklendikten sonra çalıştırılır, ancak arka plan proje yüklemesi yeniden başlamadan önce.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Bu olay, bir çözüm yük yöneticisi olup olmadığı başlangıçta tam olarak yüklendikten sonra ateşlenir. Ayrıca, çözelti tamamen yüklendiğinde arka plan yükü veya talep yükünden sonra da çalıştırılır. Aynı zamanda, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> yeniden etkinleştirilir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bu olay, bir projenin (veya projenin) yüklenmesinden önce ateşlenir. Diğer arka plan işlemlerinin projeler yüklenmeden önce `pfShouldDelayLoadToNextIdle` tamamlandığından emin olmak **için, doğru**olarak ayarlayın.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Bu olay, bir dizi proje yüklenmek üzereyken ateşlenir. Doğruysa, `fIsBackgroundIdleBatch` projeler arka planda yüklenecektir; `fIsBackgroundIdleBatch` yanlışsa, örneğin kullanıcı Çözüm Gezgini'nde bekleyen bir projeyi genişletiyorsa, projeler kullanıcı isteği nin bir sonucu olarak eşzamanlı olarak yüklenir. Aksi takdirde yapılması gereken pahalı işler yapmak için bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>olayı işleyebilir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Bu olay, bir dizi proje yüklendikten sonra ateşlenir.

## <a name="detect-and-manage-solution-and-project-loading"></a>Çözümü ve proje yüklemeyi algılama ve yönetme
 Projelerin ve çözümlerin yük durumunu saptamak için aşağıdaki değerlerle arayın: <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` çözüm ve tüm projeleri yüklenirse, aksi takdirde `false`geri döner.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` bir dizi proje şu anda arka `false`planda yükleniyorsa, aksi takdirde döndürür.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` Bir dizi proje şu anda bir kullanıcı komutu veya diğer açık `false`yük, aksi takdirde eşzamanlı olarak yükleniyorsa döndürür.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` çözüm şu anda kapalıysa döndürür, aksi takdirde. `false`

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` bir çözüm şu anda `false`açılıyorsa döndürür, aksi takdirde.

Ayrıca, aşağıdaki yöntemlerden birini arayarak projelerin ve çözümlerin yüklendiğinden emin olabilirsiniz:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: bu yöntem çağrı letme dönmeden önce yüklemek için bir çözüm projeleri zorlar.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: bu yöntem çağrılması, metot dönmeden önce projeleri `guidProject` yüklemeye zorlar.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: bu yöntem in `guidProjectID` anarak yöntem dönmeden önce projeyi yüklemeye zorlar.
