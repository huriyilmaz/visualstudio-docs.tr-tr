---
title: Bir çözümde proje yüklemeyi yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64786144"
---
# <a name="managing-project-loading-in-a-solution"></a>Bir Çözümde Proje Yüklemeyi Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio çözümleri, çok sayıda proje içerebilir. Varsayılan Visual Studio davranışı, çözüm açıldığı sırada bir Çözümdeki tüm projeleri yüklemek ve tümünün yüklemeyi bitirene kadar herhangi bir projede erişime izin vermek değildir. Proje yükleme işleminin süresi iki dakikadan uzun sürer, yüklenen proje sayısını ve toplam proje sayısını gösteren bir ilerleme çubuğu görüntülenir. Kullanıcı birden çok projeyle oluşan bir çözümde çalışırken projeleri kaldırabilirler, ancak bu yordamın bazı dezavantajları vardır: kaldırılan projeler, yeniden derleme çözümünün bir parçası olarak derlenmez ve kapalı projelerin türlerin ve üyelerinin IntelliSense açıklamaları gösterilmez.  
  
 Geliştiriciler bir çözüm yük Yöneticisi oluşturarak çözüm yükleme sürelerini azaltabilir ve proje yükleme davranışını yönetebilir. Çözüm Yükleme Yöneticisi belirli projeler veya proje türleri için farklı proje yükleme öncelikleri ayarlayabilir, bir arka plan oluşturmaya başlamadan önce projelerin yüklendiğinden, diğer arka plan görevleri tamamlanana kadar arka planda yüklemeyi geciktirdiğinden ve diğer proje yük yönetimi görevlerini gerçekleştirmede emin olun.  
  
## <a name="project-loading-priorities"></a>Proje yükleme öncelikleri  
 Visual Studio, dört farklı proje yükleme önceliği tanımlar:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (varsayılan): bir çözüm açıldığında projeler zaman uyumsuz olarak yüklenir. Bu öncelik, kaldırılmış bir projede çözüm zaten açıldıktan sonra ayarlandıysa, proje bir sonraki boşta noktaya yüklenir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: bir çözüm açıldığında, projeler arka planda yüklenir ve tüm projeler yüklenene kadar beklemek zorunda kalmadan kullanıcının projelere erişmesine izin verilir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projeler erişildiğinde yüklenir. Kullanıcı, açık belge listesinde (çözümün Kullanıcı seçenekleri dosyasında kalıcı) olduğu veya yüklenmekte olan başka bir projenin projeye bağımlılığı olduğu için, bir proje Çözüm Gezgini açtığında proje düğümünü açtığında projeye ait bir dosya açıldığında projeye erişilir. Bu proje türü, derleme işlemi başlatılmadan önce otomatik olarak yüklenmez; Çözüm yükleme yöneticisi, tüm gerekli projelerin yüklenmesini sağlamaktan sorumludur. Bu projelerin, tüm çözüm genelinde dosyalarda Bul/Değiştir başlatılmadan önce de yüklenmesi gerekir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Kullanıcı açıkça istemediği takdirde projeler yüklenmez. Bu, projelerin açıkça kaldırıldığında oluşan durumdur.  
  
## <a name="creating-a-solution-load-manager"></a>Çözüm Yükleme Yöneticisi oluşturma  
 Geliştiriciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> , çözüm yük yöneticisinin etkin olduğu Visual Studio 'yu uygulayarak ve inceleyerek çözüm yükleme yöneticisi oluşturabilir.  
  
#### <a name="activating-a-solution-load-manager"></a>Çözüm yükleme yöneticisini etkinleştirme  
 Visual Studio, belirli bir zamanda yalnızca bir çözüm yük yöneticisine izin veriyor, bu nedenle çözüm yükleme yöneticisini etkinleştirmek istediğinizde Visual Studio 'Yu uygulamalısınız. İkinci bir çözüm yükleme yöneticisi daha sonra etkinleştirilirse, çözüm yükleme yöneticinizin bağlantısı kesilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>Hizmeti almanız ve özelliği ayarlamanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> :  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Issolutionloadmanager uygulama  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>Yöntemi, çözümü açma işlemi sırasında çağrılır. Bu yöntemi uygulamak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> yönetmek istediğiniz proje türü için yük önceliğini ayarlamak üzere hizmetini kullanın. Örneğin, aşağıdaki kod C# proje türlerini arka planda yüklenecek şekilde ayarlar:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Yöntemi, Visual Studio kapatılırken veya özelliği ile çağırarak etkin çözüm yük Yöneticisi olarak farklı bir paket çekilirken çağrılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> .  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Farklı türlerde çözüm Yükleme Yöneticisi stratejileri  
 Yönetmek istediği çözüm türlerine bağlı olarak çözüm yükleme yöneticilerini farklı yollarla uygulayabilirsiniz.  
  
 Çözüm yükleme yöneticisi çözüm yüklemeyi genel olarak yönetgeliyorsa, VSPackage 'un bir parçası olarak uygulanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Bir değeri Ile VSPackage 'a eklenerek, paket, tekrar yükleme olarak ayarlanmalıdır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Çözüm yükleme yöneticisi daha sonra <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yönteminde etkinleştirilebilir.  
  
> [!NOTE]
> Paketleri oto yükleme hakkında daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).  
  
 Visual Studio yalnızca son çözüm yük yöneticisini etkinleştirecek şekilde tanıdığından, genel çözüm yükleme yöneticileri kendilerini etkinleştirmeden önce mevcut bir yük Yöneticisi olup olmadığını her zaman saptamalıdır. Geri dönüş için çözüm hizmetinde GetProperty () çağrısı yaptıysanız <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> `null` , etkin çözüm yükleme yöneticisi yoktur. Null döndürmezse, nesnenin çözüm yükleme yöneticisiyle aynı olup olmadığını kontrol edin.  
  
 Çözüm Load Manager, yalnızca birkaç tür çözümü yönetecekseniz, VSPackage çözüm yükleme olaylarına abone olabilir (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> çözüm yükleme yöneticisini etkinleştirmek için olay işleyicisini kullanabilirsiniz.  
  
 Çözüm Yükleme Yöneticisi yalnızca belirli çözümleri yönetmek için gerekliyse, etkinleştirme bilgileri çözüm dosyasının bir parçası olarak kalıcı hale gelir. Bunu yapmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> çözüm öncesi bölümüne çağrı yapın.  
  
 Belirli çözüm yükü yöneticileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> , diğer çözüm yükü yöneticileriyle çakışmayacak şekilde olay işleyicisinde kendilerini devre dışı bırakmalıdır.  
  
 Yalnızca genel proje yük önceliklerini sürdürmek için bir çözüm yükleme yöneticisi gerekiyorsa (örneğin, Seçenekler sayfasında ayarlanan özellikler), çözüm yükleme Yöneticisini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> olay işleyicisinde etkinleştirebilir, ayarı çözüm özelliklerinde kalıcı hale getirebilirsiniz, sonra çözüm yükleme yöneticisini devre dışı bırakabilirsiniz.  
  
## <a name="handling-solution-load-events"></a>Çözüm yükleme olaylarını işleme  
 Çözüm yükleme olaylarına abone olmak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> çözüm yükleme yöneticisini etkinleştirdiğinizde çağırın. Uygulamasını uygularsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , farklı proje yükleme öncelikleriyle ilgili olaylara yanıt verebilirsiniz.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bu, bir çözüm açılmadan önce tetiklenir. Çözümdeki projelerin proje yükleme önceliğini değiştirmek için bunu kullanabilirsiniz.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Bu, çözüm tamamen yüklendikten sonra, ancak arka plan projesi yüklemesi yeniden başlamadan önce tetiklenir. Örneğin, bir Kullanıcı yük önceliği gerekli olan bir projeye erişmiş olabilir veya çözüm yükleme yöneticisi, projenin arka plan yükünü Başlatan bir proje yük önceliğini BackgroundLoad olarak değiştirmiş olabilir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Bu, bir çözüm yükleme yöneticisi olup olmadığına bakılmaksızın, bir çözüm başlangıçta tam olarak yüklendikten sonra tetiklenir. Ayrıca, çözüm tam olarak yüklendiğinde arka plan yükleme veya talep yükleme sonrasında da tetiklenir. Aynı zamanda yeniden <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> etkinleştirilir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bu, bir proje (veya projeleri) yüklenmeden önce tetiklenir. Projeler yüklenmeden önce diğer arka plan işlemlerinin tamamlandığından emin olmak için, `pfShouldDelayLoadToNextIdle` **true**olarak ayarlayın.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Bu, bir proje toplu işi yüklenirken tetiklenir. `fIsBackgroundIdleBatch`True ise, projeler arka planda yüklenir; `fIsBackgroundIdleBatch` yanlışsa, bir Kullanıcı isteği sonucunda projeler zaman uyumlu olarak yüklenir; Örneğin, Kullanıcı Çözüm Gezgini bekleyen bir projeyi genişlediğinde. Bu işlemi, aksi takdirde ' de gerçekleştirilmesi gereken pahalı bir iş yapmak için uygulayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Bu, bir Batch projesi yüklendikten sonra tetiklenir.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Çözüm ve proje yüklemeyi algılama ve yönetme  
 Projelerin ve çözümlerin yüklenme durumunu algılamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> aşağıdaki değerlerle çağırın:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` `true` çözümün ve tüm projelerinin yüklenip yüklenmediğini, aksi takdirde, döndürür `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` `true` bir proje toplu işleminin şu anda arka planda yüklenmekte olup olmadığını döndürür, aksi takdirde `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` bir `true` Proje toplu işi, bir Kullanıcı komutunun veya başka bir açık yükün sonucu olarak şu anda zaman uyumlu olarak yükleniyorsa, aksi takdirde döndürür `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` `true` çözümün şu anda kapalı olup olmadığını döndürür, aksi takdirde `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` `true` çözümün şu anda açılmakta olup olmadığını döndürür, aksi takdirde `false` .  
  
  Ayrıca, aşağıdaki yöntemlerden birini çağırarak projelerin ve çözümlerin (proje yük önceliklerinden bağımsız olarak) yüklendiğinden de emin olabilirsiniz:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: Bu yöntemi çağırmak, bir çözümdeki projeleri Yöntem dönüşünden önce yüklenecek şekilde zorlar.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: Bu yöntemi çağırmak, içindeki projeleri `guidProject` Yöntem dönüşden önce yüklemeye zorlar.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: Bu yöntemi çağırmak, öğesini `guidProjectID` metot dönüşden önce yüklemeye zorlar.  
  
> [!NOTE]
> . Varsayılan olarak, yalnızca istek yükü ve arka plan yük öncelikleri olan projeler yüklenir, ancak <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> bayrak yöntemine geçirildiyse, açıkça yüklenecek şekilde işaretlenmiş olanlar hariç tüm projeler yüklenir.
