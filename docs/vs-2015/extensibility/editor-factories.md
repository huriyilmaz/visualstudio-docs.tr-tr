---
title: Düzenleyici fabrikaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197760"
---
# <a name="editor-factories"></a>Düzenleyici Fabrikaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir düzenleyici fabrikası, düzenleyici nesneleri oluşturur ve bunları fiziksel görünüm olarak bilinen bir pencere çerçevesine koyar. Düzenleyicilerin ve tasarımcıların oluşturulması için gereken belge verilerini ve belge görünümü nesnelerini oluşturur. Visual Studio temel düzenleyicisini ve herhangi bir standart düzenleyiciyi oluşturmak için bir düzenleyici fabrikası gereklidir. Özel bir düzenleyici, isteğe bağlı olarak bir düzenleyici fabrikası ile de oluşturulabilir.  
  
 Arabirimini uygulayarak bir düzenleyici fabrikası oluşturursunuz <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> . Aşağıdaki örnek, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> bir düzenleyici fabrikası oluşturmak için nasıl uygulanacağını göstermektedir:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Düzenleyici, bu düzenleyici tarafından işlenen bir dosya türünü ilk açışınızda yüklenir. Belirli bir düzenleyiciyi ya da varsayılan düzenleyiciyi açmayı seçebilirsiniz. Varsayılan düzenleyiciyi seçerseniz, tümleşik geliştirme ortamı (IDE) açılacak doğru düzenleyiciyi belirler ve ardından açar. Daha fazla bilgi için bkz. [bir projede dosya açan düzenleyiciyi belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Düzenleyici fabrikalarını kaydetme  
 Oluşturduğunuz bir düzenleyiciyi kullanabilmeniz için önce, kendisi hakkındaki bilgileri, işleyebileceği dosya uzantıları da dahil olmak üzere kaydetmeniz gerekir.  
  
 VSPackage yönetilen kodda yazılmışsa, <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> VSPackage yüklendikten sonra düzenleyici fabrikasını kaydetmek Için yönetilen paket çerçevesi (MPF) yöntemini kullanabilirsiniz. VSPackage, yönetilmeyen kodda yazılmışsa, hizmeti kullanarak düzenleyici fabrikasını kaydetmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> .  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Yönetilen kod kullanarak bir düzenleyici fabrikası kaydetme  
 Düzenleyici fabrikanızı VSPackage 'un yöntemine kaydetmeniz gerekir `Initialize` . İlk çağrı `base.Initialize` yapın ve ardından <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> her bir düzenleyici fabrikası için çağırın  
  
 Yönetilen kodda, VSPackage bunu sizin için işleyeceğinden, bir düzenleyici fabrikasının kaydını kaldırmanız gerekmez. Ayrıca, düzenleyici fabrikası uygularsa <xref:System.IDisposable> , kayıt edildiğinde otomatik olarak uygulanır.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Yönetilmeyen kod kullanarak bir düzenleyici fabrikası kaydetme  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>Düzenleyici paketinizin uygulamasında `QueryService` çağırmak için yöntemini kullanın `SVsRegisterEditors` . Bunu yapmak için bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>Arabirim uygulamanızı geçirerek yöntemi çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> . Ayrı bir sınıfta ygula yapmanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
## <a name="the-editor-factory-registration-process"></a>Düzenleyici fabrikası kayıt Işlemi  
 Visual Studio düzenleyiciniz düzenleyici fabrikanızı kullanarak yüklediğinde aşağıdaki süreç gerçekleşir:  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Proje sistemi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Bu yöntem, düzenleyici fabrikasını döndürür. Ancak, bir proje sistemi düzenleyiciye ihtiyaç duyuncaya kadar, düzenleyicinin paketini yüklerken Visual Studio gecikmeleri olur.  
  
3. Bir proje sistemi düzenleyiciye ihtiyaç duyduğunda, Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> hem belge görünümü hem de belge veri nesneleri döndüren özel bir yöntem çağırır.  
  
4. Visual Studio 'Yu kullanarak düzenleyici fabrikanıza <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> bir belge veri nesnesi ve belge görünümü nesnesi Döndür ' i kullanırsanız, Visual Studio belge penceresini oluşturur, belge görünümü nesnesini buna koyar ve belge veri nesnesi için çalışan belge tablosuna (RDT) bir giriş yapar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Çalıştırılan Belge Tablosu](../extensibility/internals/running-document-table.md)
