---
title: Çözüm Project Yüklemesini Yönetme | Microsoft Docs
description: Geliştiricilerin çözüm yük yöneticisi oluşturarak çözüm yükleme sürelerini azaltmayı ve proje yükleme davranışını yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a832cfe0638a0590d5950022c2cfa44a91ce1654713872d89c7faa985c0679a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388519"
---
# <a name="manage-project-loading-in-a-solution"></a>Bir çözümde proje yüklemesini yönetme
Visual Studio çözümleri çok sayıda proje içerebilir. Varsayılan Visual Studio davranışı, çözümün aç olduğu anda bir çözüme tüm projeleri yüklemek ve kullanıcının tüm projelerin yüklemesi tamam olana kadar herhangi bir projeye erişmesine izin vermek değildir. Proje yükleme işlemi iki dakikadan uzun sürerse, yüklenen proje sayısını ve toplam proje sayısını gösteren bir ilerleme çubuğu görüntülenir. Kullanıcı birden çok proje içeren bir çözümde çalışırken projeleri kaldırabilirsiniz, ancak bu yordamın bazı dezavantajları vardır: kaldırılan projeler Çözümü Yeniden Oluştur komutunun bir parçası olarak oluşturmaz ve kapalı projelerin türleri ve üyelerinin IntelliSense açıklamaları görüntülenmez.

 Geliştiriciler çözüm yük yöneticisi oluşturarak çözüm yükleme sürelerini düşürerek proje yükleme davranışını yönetebilir. Çözüm yük yöneticisi, bir arka plan derlemesini başlatmadan önce projelerin yüklendiğinden emin olabilir, diğer arka plan görevleri tamamlayana kadar arka plan yüklemesini geciktirebilir ve diğer proje yükü yönetim görevlerini gerçekleştirebilir.

## <a name="create-a-solution-load-manager"></a>Çözüm yük yöneticisi oluşturma
 Geliştiriciler, çözüm yük yöneticisinin etkin olduğu bir uygulama ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Visual Studio çözüm yük yöneticisi oluşturabilir.

### <a name="activate-a-solution-load-manager"></a>Çözüm yük yöneticisini etkinleştirme
 Visual Studio aynı anda yalnızca bir çözüm yük yöneticisine izin verir, bu nedenle Visual Studio yük yöneticinizi ne zaman etkinleştirmek istediğiniz konusunda öneride bulundurabilirsiniz. İkinci bir çözüm yük yöneticisi daha sonra etkinleştirilirse çözüm yük yöneticinizin bağlantısı kesilir.

 Hizmeti alı <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> ve [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 yöntemi, Visual Studio kapatılarak veya farklı bir paket etkin çözüm yük yöneticisi olarak iş yükü yöneticisi olarak ele <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) özelliği.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Farklı çözüm yük yöneticisi türleri için stratejiler
 Çözüm yük yöneticilerini yönetmeye yönelik çözüm türlerine bağlı olarak farklı şekillerde gerçekleştirebilirsiniz.

 Çözüm yük yöneticisinin genel olarak çözüm yüklemesini yönetmesi amaçlandı ise, vsPackage'ın bir parçası olarak uygulan olabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Paketin, DEĞERIyle VSPackage'a ek olarak otomatik yükleme olarak ayarlanmış olması <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> gerekir. Çözüm yük yöneticisi daha sonra yönteminde <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> etkinleştirilebilir.

> [!NOTE]
> Paketleri otomatik yükleme hakkında daha fazla bilgi için [bkz. VSPackage'ları Yükleme.](../extensibility/loading-vspackages.md)

 Genel Visual Studio yalnızca etkinleştirilen son çözüm yük yöneticisini tanıması, genel çözüm yük yöneticilerinin kendilerini etkinleştirmeden önce mevcut bir yük yöneticisi olup olmadığını her zaman algılaması gerekir. Sorun için `GetProperty()` çözüm hizmetine çağrı [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null` döndürse de etkin bir çözüm yük yöneticisi yoktur. Null döndürene kadar nesnenin çözüm yük yöneticinizle aynı olup olmadığını kontrol edin.

 Çözüm yük yöneticisinin yalnızca birkaç çözüm türü yönetmesi amaçlı ise VSPackage çözüm yükleme olaylarını (çağırarak) abone olabilir ve çözüm yük yöneticisini etkinleştirmek için için olay <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> işleyicisini kullanabilir.

 Çözüm yük yöneticisi yalnızca belirli çözümleri yönetmeye yönelikse, etkinleştirme bilgileri çözüm öncesi bölümü çağrılarak çözüm dosyasının bir parçası <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> olarak kalıcı olabilir.

 Belirli çözüm yük yöneticilerinin diğer çözüm yük yöneticileriyle çakışmamaları için kendilerini olay <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> işleyicisinde devre dışı bırakmaları gerekir.

 Yalnızca genel proje yükleme özelliklerini kalıcı hale getiren bir çözüm yük yöneticisine ihtiyacınız varsa (örneğin, seçenekler sayfasında ayarlanmış özellikler), olay işleyicisinde çözüm yük yöneticisini etkinleştirebilirsiniz, çözüm özelliklerinde ayarı kalıcı hale getirebilirsiniz ve ardından çözüm yük yöneticisini devre dışı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> abilirsiniz.

## <a name="handle-solution-load-events"></a>Çözüm yükleme olaylarını işleme
 Çözüm yükleme olaylarını abone olmak için çözüm <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> yük yöneticinizi etkinleştirirken çağrısı yapmak. uygulamasına sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> olursanız, farklı proje yükleme özellikleriyle ilgili olaylara yanıt veabilirsiniz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bu olay bir çözüm açık olmadan önce başlatıldı.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Çözüm tamamen yüklendikten sonra ama arka plan projesi yüklemesi yeniden başlamadan önce bu olay başlatıldı.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Çözüm yük yöneticisi olup olmadığıyla ilgili bir çözüm başlangıçta tamamen yüklendikten sonra bu olay başlatıldı. Çözüm tam olarak yüklendiğinde arka plan yükü veya talep yükü sonrasında da bu sorun ortaya çıktı. Aynı zamanda, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> yeniden etkinleştirildi.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bu olay bir proje (veya proje) yüklemeden önce başlatıldı. Projeler yüklenmeden önce diğer arka plan işlemlerinin tamamlandığından emin olmak için true `pfShouldDelayLoadToNextIdle` olarak **ayarlayın.**

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Bir proje toplu işi yüklenmek için hazır olduğunda bu olay başlatıldı. True ise, projeler arka planda yüklenir; false ise, projeler bir kullanıcı isteğinin sonucu olarak zaman uyumlu olarak yüklenecektir( örneğin, kullanıcı Çözüm Gezgini'de bekleyen bir projeyi `fIsBackgroundIdleBatch` `fIsBackgroundIdleBatch` genişletiyorsa). Aksi takdirde içinde yapılması gereken pahalı işler yapmak için bu olayı işleysiniz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Bir proje toplu işi yüklendikten sonra bu olay başlatıldı.

## <a name="detect-and-manage-solution-and-project-loading"></a>Çözümü ve proje yüklemesini algılama ve yönetme
 Projelerin ve çözümlerin yük durumunu algılamak için aşağıdaki <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> değerlerle çağrısı yapın:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` `true` çözümün ve tüm projelerinin yüklü olduğu durumda `false` döndürür.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>)şu anda arka planda bir proje toplu işi yüklü ise `var` `true` döndürür, aksi takdirde `false` döndürür.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>)bir proje toplu işi kullanıcı komutunun veya diğer açık yükün sonucu olarak zaman uyumlu olarak yükleniyorsa `var` `true` döndürür, aksi takdirde `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` çözüm `true` şu anda kapatılacaksa döndürür, değilse `false` döndürür.

- [__VSPROPID. VSPROPID_IsSolutionOpening:](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>)bir `var` `true` çözüm şu anda açıksa döndürür, değilse `false` döndürür.

Ayrıca aşağıdaki yöntemlerden birini çağırarak projelerin ve çözümlerin yüklendiğinden emin olun:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: bu yöntemin çağrılarak çözümde yer alan projeler, yöntem dönüşmeden önce yüklenmeye devam ediyor.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: bu yöntemin çağrılarak, yöntemi `guidProject` geri dönüşden önce içinde projelerin yüklenmeye zorunda olduğu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: bu yöntemin çağrılsı, yöntemi `guidProjectID` geri dönüşden önce projeyi yüklemeye güç sağlar.
