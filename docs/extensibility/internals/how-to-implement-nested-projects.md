---
title: 'Nasıl yapılır: Iç Içe Projeler uygulama | Microsoft Docs'
description: bir proje hiyerarşisi oluşturmak için çözüm ve üst projelerden olayları yükselterek Visual Studio iç içe projeler uygulamayı nasıl uygulayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: de258e2b1ca7f57573a1e79d33c6a80960325d3662c8af9ce9e8111a330b6f12
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359318"
---
# <a name="how-to-implement-nested-projects"></a>Nasıl yapılır: iç içe Projeler uygulama

İç içe geçmiş bir proje türü oluşturduğunuzda, uygulanması gereken birkaç ek adım vardır. Bir üst proje, çözümün iç içe geçmiş (alt) projelerine yönelik aynı sorumlulukların bazılarını alır. Üst proje, bir çözüme benzer bir proje kapsayıcısıdır. Özellikle, iç içe projeler hiyerarşisini oluşturmak için çözüm tarafından ve ana projeler tarafından oluşturulması gereken birkaç olay vardır. Bu olaylar, iç içe projeler oluşturmak için aşağıdaki işlemde açıklanmıştır.

## <a name="create-nested-projects"></a>İç içe projeler oluşturma

1. Tümleşik geliştirme ortamı (IDE), arabirimi çağırarak ana projenin proje dosyasını ve başlangıç bilgilerini yükler <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> . Üst proje oluşturulup çözüme eklenir.

    > [!NOTE]
    > Bu noktada, üst projenin alt projeler oluşturulmadan önce oluşturulması gerektiğinden, ana projenin iç içe proje oluşturması için çok erken bir işlemdir. Bu sırayı takip eden ana proje, alt projelere ayarları uygulayabilir ve alt projeler gerekirse ana projelerden bilgi alabilir. Bu sıra, kaynak kodu denetimi (SCC) ve **Çözüm Gezgini** gibi istemciler tarafından gerek duyuluyordu.

     Üst proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> iç içe geçmiş (alt) proje veya projelerini oluşturabilmeniz için YÖNTEMIN IDE tarafından çağrılması için beklemeniz gerekir.

2. IDE, `QueryInterface` için üst projede çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Bu çağrı başarılı olursa, IDE üst <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> projenin tüm iç içe projelerini açmak için üst öğenin yöntemini çağırır.

3. Üst proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> iç içe projeler oluşturulacak dinleyicileri bilgilendirmek için yöntemini çağırır. SCC, örneğin, çözüm ve proje oluşturma işlemindeki adımların sırayla oluşup oluşmadığını bildirmek üzere bu olayları dinler. Adımlar sıra dışında oluşursa, çözüm kaynak kodu denetimine doğru şekilde kaydettirilmemiş olabilir.

4. Üst proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> alt projelerinin her birinde yöntemini veya yöntemini çağırır.

     <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `AddVirtualProject` Sanal (iç içe) projenin proje penceresine eklenmesi, derlemeden hariç tutulması, kaynak kodu denetimine eklenmesi ve bu şekilde devam etmesi gerektiğini göstermek için yöntemine geçiş yapabilirsiniz. `VSADDVPFLAGS` iç içe geçmiş projenin görünürlüğünü denetlemenize ve bununla hangi işlevlerin ilişkilendirildiğini belirtebilmenizi sağlar.

     Üst projenin proje dosyasında depolanan bir proje GUID 'SI olan önceden varolan bir alt projeyi yeniden yüklerseniz, ana proje çağırır `AddVirtualProjectEx` . Ve arasındaki tek fark `AddVirtualProject` , `AddVirtualProjectEX` `AddVirtualProjectEX` üst projenin `guidProjectID` etkinleştirilecek <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> ve doğru çalışması için alt projenin örnek başına bir örnek belirtmesini sağlayan bir parametreye sahiptir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> .

     Kullanılabilir bir GUID yoksa (örneğin, yeni bir iç içe geçmiş proje eklediğinizde), çözüm proje için üst öğeye eklendiği sırada bir tane oluşturur. Bu proje GUID 'sinin proje dosyasında kalıcı hale getirilmesi için üst projenin sorumluluğundadır. İç içe geçmiş bir projeyi silerseniz, söz konusu projenin GUID 'i de silinebilir.

5. IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> üst projenin her bir alt projesinde yöntemini çağırır.

     `IVsParentProject`Projeleri iç içe aktarmak istiyorsanız üst projenin uygulanması gerekir. Ancak üst proje, `QueryInterface` `IVsParentProject` altında üst projelere sahip olsa bile hiçbir şekilde hiçbir şekilde çağırılmaz. Çözümü öğesine yapılan çağrıyı işler `IVsParentProject` ve uygulanmışsa, `OpenChildren` iç içe projeler oluşturmak için çağırır. `AddVirtualProjectEX` her zaman öğesinden çağırılır `OpenChildren` . Hiyerarşi oluşturma olaylarını sırasıyla tutmak için asla ana proje tarafından çağrılmamalıdır.

6. IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> yöntemi alt projede çağırır.

7. Üst proje, üst öğe <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> için alt projelerin oluşturulduğu dinleyicileri bilgilendirmek için yöntemini çağırır.

8. IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> tüm alt projeler açıldıktan sonra üst projede yöntemini çağırır.

     Zaten yoksa, üst proje çağırarak her iç içe proje için bir GUID oluşturur `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` , bir GUID oluşturulduğunda çağrılan bir COM API 'sidir. Daha fazla bilgi için `CoCreateGuid` MSDN Kitaplığı 'ndaki ve GUID 'ler bölümüne bakın.

     Üst proje, bu GUID 'yi proje dosyasında, IDE 'de bir sonraki sefer açıldığında elde edilecek şekilde depolar. `AddVirtualProjectEX`Alt proje için öğesini almak üzere öğesinin çağrılması ile ilgili daha fazla bilgi için bkz `guidProjectID` . 4. adım.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Daha sonra yöntemi, Iç öğe öğesi için ' de, iç içe geçmiş projede temsilci seçtiğiniz kurala göre çağırılır. , <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Üst öğede çağrıldığında temsilci seçmek istediğiniz bir projeyi hedefleyen düğümün özelliklerini alır.

     Üst ve alt projeler programlı bir şekilde örneklendiği için, bu noktada iç içe projeler için özellikler ayarlayabilirsiniz.

    > [!NOTE]
    > Yalnızca iç içe geçmiş projeden bağlam bilgilerini almayın, ancak __VSHPROPID denetleyerek üst projede bu öğe için herhangi bir bağlam olup olmadığını da isteyebilirsiniz [. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Bu şekilde, tek tek iç içe projelere özel ek dinamik yardım öznitelikleri ve menü seçenekleri ekleyebilirsiniz.

10. Hiyerarşi, yöntemi çağrısıyla birlikte **Çözüm Gezgini** görüntülenmek üzere oluşturulmuştur <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .

     `GetNestedHierarchy`Çözüm Gezgini ' de görüntüleme hiyerarşisi oluşturmak için hiyerarşiyi ortamına geçirin. Bu şekilde, çözüm projenin var olduğunu ve yapı yöneticisi tarafından oluşturma için yönetilebilecek olduğunu bilir ya da projedeki dosyaların kaynak kodu denetimi altına yerleştirilmesine izin verebilir.

11. Project1 için tüm iç içe projeler oluşturulduğunda denetim çözüme geri geçirilir ve işlem Project2 için yinelenir.

     İç içe projeler oluşturmak için aynı işlem, alt öğesi olan bir alt proje için oluşur. Bu durumda, bir Project1 alt öğesi olan BuildProject1, alt projeler içeriyorsa, BuildProject1 ve Before Project2 sonrasında oluşturulur. İşlem özyinelemeli ve hiyerarşi yukarıdan aşağı doğru oluşturulmuştur.

     İç içe geçmiş bir proje kapatıldığında, Kullanıcı çözümü veya belirli bir projeyi kapattığından, üzerindeki diğer yöntemi `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> çağrılır. Üst proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> ve, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> iç içe geçmiş projelerin kapatılmakta olduğu çözüm olaylarına dinleyicileri bildirmek için ve yöntemleri ile yöntemine çağrıları kaydırır.

Aşağıdaki konular, iç içe projeler uygularken dikkate alınması gereken birkaç diğer kavram ile ilgilidir:

- [İç içe projeleri kaldırma ve yeniden yükleme konuları](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [İç içe projeler için sihirbaz desteği](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [İç içe projeler için komut işlemeyi Uygula](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [İç içe projeler için AddItem iletişim kutusunu filtrele](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
- [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbaz (. vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
