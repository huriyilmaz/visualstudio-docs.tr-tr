---
title: 'Nasıl yapılır: düzenleyiciler için bağlam sağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858308"
---
# <a name="how-to-provide-context-for-editors"></a>Nasıl Yapılır: Düzenleyiciler İçin Bağlam Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir düzenleyici için bağlam yalnızca Düzenleyici odağa sahip olduğunda veya odak bir araç penceresine taşınmadan hemen önce odağa sahip olduğunda etkindir. Aşağıdaki işlemleri gerçekleştirerek bir düzenleyici için bağlam sağlayabilirsiniz:  
  
1. Bağlam paketi oluşturun.  
  
2. Bağlam paketini seçim öğesi tanımlayıcısına (SEıD) yayımlayın.  
  
3. İçeriği pakette saklayın.  
  
   Bu görevler aşağıdaki yordamlar tarafından ele alınmıştır. Bağlam sağlama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında daha sonra **dayanıklı programlama** bölümüne bakın.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Bir düzenleyici veya tasarımcı için bağlam paketi oluşturmak için  
  
1. `QueryService` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Hizmet için arabiriminize çağrı yapın <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> .  
  
     Arabirime yönelik bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> döndürülür.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>Yeni bir bağlam veya alt bağlam paketi oluşturmak için yöntemini çağırın.  
  
     Arabirime yönelik bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> döndürülür.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>Bağlam veya alt bağlam çantasına öznitelikler, arama anahtar sözcükleri veya F1 anahtar sözcükleri eklemek için yöntemini çağırın.  
  
4. Bir alt bağlam paketi oluşturuyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> alt bağlam paketini üst bağlam çantasına bağlamak için yöntemini çağırın.  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> **Dinamik yardım** penceresi güncelleştirmek üzere olduğunda bildirim almak için çağrısı yapın.  
  
     Güncelleştirme gerçekleşene kadar, **dinamik yardım** penceresinin düzenleyicinizi çağırmasını sağlamak, bu sayede,, güncelleştirme gerçekleşene kadar bağlam değiştirmeyi gecikme fırsatı verir. Bunun yapılması, Sistem boşta kalma süresi kullanılabilir olana kadar zaman alan algoritmaların çalışmasını ertelemenize olanak sağladığından performansı iyileştirebilir.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Bağlam paketini SEıD 'ye yayımlamak için  
  
1. `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Arabirime bir işaretçi döndürmek için hizmette çağrı yapın <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> .  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> `elementid` Genel düzeye bağlam geçirdiğimizden emin olmak için SEID_UserContext bir öğe tanımlayıcı (parametre) değeri belirterek çağırın.  
  
3. Düzenleyici veya tasarımcı etkin hale geldiğinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> nesnesindeki değerler genel seçime yayılır. Bu işlemi her oturum için yalnızca bir kez gerçekleştirmeniz gerekir ve sonra işaretçiyi, çağrıldığında oluşturulan genel bağlam için saklayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Bağlam çantasından korumak için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> **Dinamik yardım** penceresinin, yapılandırmadan önce düzenleyiciyi veya tasarımcıyı çağırdığından emin olmak için uygulamasını uygulayın.  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>Bağlam paketi oluşturulduktan ve uygulandıktan sonra çağrılan her bir bağlam paketi için, IDE, bağlam <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> paketi 'nin güncelleştirileceği bağlam sağlayıcısına bildirimde bulunur. Bu çağrıyı, bağlam çantasındaki öznitelikleri ve anahtar sözcükleri ve **dinamik yardım** penceresi güncelleştirmesi gerçekleşmeden önce herhangi bir alt bağlam çantasında değiştirmek için kullanabilirsiniz.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>Düzenleyicinin veya tasarımcının yeni bir bağlam olduğunu göstermek için bağlam çantasında çağrı yapın.  
  
     **Dinamik yardım** penceresi güncelleştirildiğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> göstermek için çağırdığında, düzenleyici veya tasarımcı, bağlamı hem üst bağlam paketi hem de o anda herhangi bir alt bağlam paketleri için uygun şekilde güncelleştirebilir.  
  
    > [!NOTE]
    > Bayrak, bağlam `SetDirty` `true` çantasından her içerik eklendiğinde veya kaldırıldığında otomatik olarak ayarlanır. **Dinamik yardım** penceresi yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> bayrak olarak ayarlandıysa bağlam çantasında çağrılır `SetDirty` `true` . Güncelleştirme sonrasında olarak sıfırlanır `false` .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>Etkin bağlam koleksiyonuna bağlam eklemek veya bağlamı kaldırmak için çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kendi düzenleyicinizi yazıyorsanız, düzenleyiciye bağlam sağlamak için bu konudaki yordamların üçünü de doldurmanız gerekir.  
  
> [!NOTE]
> Bir düzenleyiciyi veya tasarımcı penceresini düzgün bir şekilde etkinleştirmek ve komut yönlendirmesinin doğru şekilde güncelleştirildiğinden emin olmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> bileşeni odak penceresi yapmak üzere çağırmanız gerekir.  
  
 SEıD, seçime göre değişen özelliklerin bir koleksiyonudur. SEıD bilgileri genel seçim üzerinden kullanılabilir. Genel seçim, arabirimi tarafından tetiklenen olaylara bağlanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> ve seçilen her şeyin (geçerli düzenleyici, geçerli araç penceresi, geçerli hiyerarşi vb.) bir listesini içerir.  
  
 Düzenleyici ve tasarımcılar için, imleç bir sözcük içinde her taşınışınızda içeriğin değiştirebileceği, bağlam çantasında sürekli olarak güncelleştirilmesi verimsiz olur. Daha verimli bir şekilde güncelleştirmek için işaretçiyi düzenleyici veya tasarımcı penceresinde herhangi bir kez daha verimli hale getirmek için öğesini çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Bunun yapılması, boşta kalma süresi ve IDE 'nin bağlam hizmeti, **dinamik yardım** penceresinin güncelleyen düzenleyiciye veya tasarımcıya bildirim gönderene kadar bağlam değişikliklerinizi tutamanızı sağlar. Bu yaklaşım, bu konudaki "bağlam çantasından korumak Için" yordamında kullanılır.  
  
 Düzenleyiciniz veya tasarımcı içindeki etkinlikler için bağlam sağladıktan sonra, kullanıcıların düzenleyici veya tasarımcı için yardım almasını sağlamak üzere belirli bir F1 anahtar sözcüğü sağlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
