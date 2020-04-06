---
title: 'Nasıl Yapılsın: İç Içe Projeler | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707980"
---
# <a name="how-to-implement-nested-projects"></a>Nasıl Yapılsın: İç içe projeler uygulama

İç içe bir proje türü oluşturduğunuzda, uygulanması gereken birkaç ek adım vardır. Bir üst proje, çözümün iç içe geçen (alt) projeleri için sahip olduğu bazı sorumlulukları üstlenir. Ana proje, çözüme benzer bir proje kapsayıcısır. Özellikle, iç içe projeler hiyerarşisi oluşturmak için çözüm ve üst projeler tarafından yükseltilmesi gereken çeşitli olaylar vardır. Bu olaylar iç içe projeler oluşturmak için aşağıdaki süreçte açıklanmıştır.

## <a name="create-nested-projects"></a>İç içe projeler oluşturma

1. Tümleşik geliştirme ortamı (IDE), arabirimi arayarak ana projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> proje dosyasını ve başlangıç bilgilerini yükler. Ana proje oluşturulur ve çözüme eklenir.

    > [!NOTE]
    > Bu noktada, ana projenin iç içe geçen projeyi oluşturması için çok erken, çünkü alt projeler oluşturulmadan önce ana projenin oluşturulması gerekir. Bu sırayı takiben, ana proje alt projelere ayarlar uygulayabilir ve alt projeler gerekirse ana projelerden bilgi alabilir. Bu sıra, kaynak kodu denetimi (SCC) ve Solution **Explorer**gibi istemciler tarafından ihtiyaç duyulur.

     Ana proje, iç <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> içe (alt) proje veya projeleri oluşturabilmesi için yöntemin IDE tarafından çağrılmasını beklemelidir.

2. IDE, `QueryInterface` ana projeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Bu çağrı başarılı olursa, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> ana proje için iç içe geçen tüm projeleri açmak için üst yöntemi çağırır.

3. Ana proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> iç içe olan projelerin oluşturulmak üzere olduğunu dinleyicilere bildirmek için yöntemi çağırır. Örneğin SCC, çözüm ve proje oluşturma sürecindeki adımların sırayla oluşup oluşmadiğini öğrenmek için bu olayları dinliyor. Adımlar sıra dışı gerçekleşirse, çözüm kaynak kodu denetimine doğru kaydedilmemiş olabilir.

4. Ana proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> alt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> projelerinin her birinde metodu veya yöntemi çağırır.

     Sanal <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> (iç `AddVirtualProject` içe) projenin proje penceresine eklenmesi, yapının dışında, kaynak kodu denetimine eklenmesi vb. belirtilmesi gerektiğini belirtmek için yönteme geçersiniz. `VSADDVPFLAGS`iç içe olan projenin görünürlüğünü denetlemenize ve hangi işlevin onunla ilişkili olduğunu belirtmenize olanak tanır.

     Ana projenin proje dosyasında guid depolanmış bir proje guid'i olan daha önce varolan `AddVirtualProjectEx`bir alt projeyi yeniden yüklerseniz, ana proje çağırır. `AddVirtualProject` Arasındaki tek `AddVirtualProjectEX` fark, `AddVirtualProjectEX` ana projenin alt proje için bir örnek `guidProjectID` başına etkinleştirmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> doğru çalışması için bir örnek belirtmek için etkinleştirmek için bir parametre olmasıdır.

     Yeni bir iç içe proje eklediğinizde olduğu gibi kullanılabilir GUID yoksa, çözüm üst öğeye eklendiğinde proje için bir tane oluşturur. Bu proje GUID'i proje dosyasında sürdürmek ana projenin sorumluluğundadır. İç içe bir projeyi silerseniz, bu projenin GUID'i de silinebilir.

5. IDE, ana <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> projenin her alt projesindeki yöntemi çağırır.

     Projeleri yuvalamak `IVsParentProject` istiyorsanız ana projeyi uygulamanız gerekir. Ancak ana proje, `QueryInterface` `IVsParentProject` altında ana projeler olsa bile asla çağrılmaz. Çözüm çağrıyı `IVsParentProject` işler ve uygulanırsa iç içe `OpenChildren` yönelik projeler oluşturmak için çağırır. `AddVirtualProjectEX`her zaman `OpenChildren`denir . Hiyerarşi oluşturma olaylarını düzenli tutmak için ana proje tarafından asla çağrılmamalıdır.

6. IDE, alt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> projedeki yöntemi çağırır.

7. Üst proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> dinleyicilere üst öğe için alt projelerin oluşturulduğunu bildirmek için yöntemi çağırır.

8. Tüm alt projeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> açıldıktan sonra IDE ana projedeki yöntemi çağırır.

     Zaten yoksa, ana proje arayarak `CoCreateGuid`iç içe geçen her proje için bir GUID oluşturur.

    > [!NOTE]
    > `CoCreateGuid`GUID oluşturulacaksa çağrılan bir COM API'sidir. Daha fazla bilgi `CoCreateGuid` için MSDN Kitaplığı'nda guid'lere bakın.

     Ana proje, bu GUID'i IDE'de bir sonraki açıldığında alınacak proje dosyasında depolar. Çocuk projesiiçin geri alma çağrısıyla `AddVirtualProjectEX` ilgili `guidProjectID` daha fazla bilgi için adım 4'e bakın.

9. Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> daha sonra iç içe proje için temsilci kongre tarafından ana ItemID için çağrılır. Üst <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> öğeye çağrıldığında devretmek istediğiniz bir projeyi iç içe alan düğümün özelliklerini alır.

     Üst ve alt projeler programlı olarak anında olduğundan, bu noktada iç içe geçen projeler için özellikler ayarlayabilirsiniz.

    > [!NOTE]
    > İç içe olan projeden bağlam bilgilerini almakla birlikte, ana projenin __VSHPROPID denetleyerek bu öğe için herhangi bir bağlam ı olup olmadığını da [sorabilirsiniz. VSHPROPID_UserContext.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>) Bu şekilde, tek tek iç içe projelere özgü ekstra dinamik yardım öznitelikleri ve menü seçenekleri ekleyebilirsiniz.

10. Hiyerarşi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> çözüm için bir çağrı ile **Çözüm Gezgini** görüntülemek için oluşturulur.

     Çözüm Gezgini'nde görüntülenmek `GetNestedHierarchy` üzere hiyerarşi oluşturmak için hiyerarşiyi ortama geçirirsiniz. Bu şekilde, çözüm projenin var olduğunu ve yapı yöneticisi tarafından oluşturmak için yönetilebilir veya projedeki dosyaların kaynak kodu denetimi altına alınmasına izin verebilir bilir.

11. Project1 için iç içe geçmiş tüm projeler oluşturulduğunda, denetim çözüme geri aktarılır ve proje2 için işlem yinelenir.

     İç içe geçen projeler oluşturmak için aynı işlem, alt projesi olan bir alt proje için de gerçekleşir. Bu durumda, Project1'in bir çocuğu olan BuildProject1'in alt projeleri varsa, bunlar BuildProject1'den sonra ve Project2'den önce oluşturulur. İşlem özyinelemelidir ve hiyerarşi yukarıdan aşağıya doğru oluşturulur.

     Kullanıcı çözümü veya belirli projenin kendisini kapattığı için iç içe geçen `IVsParentProject`bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>proje kapatıldığında, diğer yöntem , , Ana proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> çağrıları yönteme, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> dinleyicilere iç içe olan projelerin kapatıldığını çözüm olaylarına bildiren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> yöntemlerle sarar.

Aşağıdaki konular, iç içe geçen projeleri uygularken göz önünde bulundurulması gereken diğer birkaç kavramla ilgilidir:

- [İç içe olan projelerin boşaltılması ve yeniden yüklenmesi nde dikkat edilmesi gerekenler](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe projeler için sihirbaz desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [İç içe projeler için komut işlemeyi uygulama](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe geçmiş projeler için AddItem iletişim kutusunu filtreleme](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Denetim Listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
