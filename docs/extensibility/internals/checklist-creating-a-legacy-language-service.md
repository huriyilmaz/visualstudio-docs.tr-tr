---
title: 'Kontrol Listesi: Eski Dil Hizmeti Oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709783"
---
# <a name="checklist-create-a-legacy-language-service"></a>Denetim Listesi: Eski bir dil hizmeti oluşturma
Aşağıdaki denetim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] listesi, çekirdek düzenleyici için bir dil hizmeti oluşturmak için atmanız gereken temel adımları özetler. Dil hizmetinizi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]entegre etmek için hata ayıklama ifade değerlendiricisi oluşturmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcı genişletilebilirliğinde](../../extensibility/debugger/visual-studio-debugger-extensibility.md)bir [CLR ifade değerlendiricisi yazın.](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

## <a name="steps-to-create-a-language-service"></a>Dil hizmeti oluşturma adımları

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> arabirimini gerçekleştirin.

    - VSPackage'nizde, dil <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> hizmetini sağlamak için arabirimi uygulayın.

    - Dil hizmetinizi uygulamanızda tümleşik geliştirme ortamına <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (IDE) hazır hale getirin.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Arabirimi ana dil hizmeti sınıfında uygulayın.

     Arabirim, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> çekirdek düzenleyici ve dil hizmeti arasındaki etkileşimin başlangıç noktasıdır.

### <a name="optional-features"></a>İsteğe bağlı özellikler
 Aşağıdaki özellikler isteğe bağlıdır ve herhangi bir sırada uygulanabilir. Bu özellikler dil hizmetinizin işlevselliğini artırır.

- Sözdizimi boyama

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini gerçekleştirin. Bu arabirimi uygulamanız, uygun renk bilgilerini döndürmek için ayrıştırıcı bilgileri olmalıdır.

  Yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> döndürür. Her metin arabelleği için ayrı bir renklendirici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> örneği oluşturulur, bu nedenle arabirimi ayrı ayrı uygulamanız gerekir. Daha fazla bilgi için, [eski bir dil hizmetinde Sözdizimi boyama'ya](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)bakın.

- Kod penceresi

  Dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> hizmetinin yeni bir kod penceresi oluşturulduğuna İlişkin bildirimi almasını sağlamak için arabirimi uygulayın.

  Yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> döndürür. Dil hizmeti daha sonra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>kod penceresine özel ui ekleyebilir. Dil hizmeti, 'de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>metin görünümü filtresi eklemek gibi özel bir işlem de yapabilir.

- Metin görünümü filtresi

  Bir dil hizmetinde IntelliSense deyiminin tamamlanmasını sağlamak için, metin görünümünün başka şekilde işleyeceğinin bazı komutlarını engellemeniz gerekir. Bu komutları engellemek için aşağıdaki adımları tamamlayın:

  - Komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zincirine katılmak ve editör komutlarını işlemek için uygulayın.

  - <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Yöntemi arayın ve uygulamanızda geçirin. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

  - Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> komutların artık size geçirilemeyecek şekilde görünümden ayrılırken yöntemi arayın.

  İşlemesi gereken komutlar sağlanan hizmetlere bağlıdır. Daha fazla bilgi [için, dil hizmeti filtreleri için önemli komutlara](../../extensibility/internals/important-commands-for-language-service-filters.md)bakın.

  > [!NOTE]
  > Arabirim, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimle aynı nesne üzerinde uygulanmalıdır.

- İfade tamamlama

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimini gerçekleştirin.

  İfade tamamlama komutunu destekleyin <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(diğer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> bir deyişle) ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimden geçerek arabirimdeki yöntemi çağırın. Daha fazla bilgi için, [eski bir dil hizmetinde Deyim tamamlama'ya](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)bakın.

- Yöntem ipuçları

  Yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> ipucu penceresi için veri sağlamak için arabirimi uygulayın.

  Yöntem veri ipucu penceresinin ne zaman gösterilebildiğini bilmek için komutları uygun şekilde işlemek için metin görünümü filtresini yükleyin. Daha fazla bilgi [için, eski bir dil hizmetinde Parametre Bilgileri'ne](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)bakın.

- Hata işaretleri

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirimini gerçekleştirin.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Arabirimi uygulayan hata işaretçisi nesnelerini oluşturun ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> hata işaretçisi nesnesinin arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> geçerek yöntemi çağırın.

  Genellikle her hata işaretçisi görev listesi penceresinde bir öğe yönetir.

- Görev listesi öğeleri

  Arabirimi sağlayan bir görev <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> öğesi sınıfı uygulayın.

  Arabirimi ve arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> sağlayan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> görev sağlayıcı sınıfı uygulayın.

  Arabirimi sağlayan bir görev eleme sınıfı <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> uygulayın.

  Görev sağlayıcısını görev listesinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> yöntemiyle kaydedin.

  Dil <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> hizmetinin hizmet sağlayıcısını GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>hizmetiyle arayarak arabirimi edinin.

  Görev öğesi nesneleri oluşturun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> ve yeni <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> veya güncelleştirilmiş görevler olduğunda arabirimdeki yöntemi çağırın.

- Görev öğelerini açıklama

  Açıklama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> görev belirteçleri elde etmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> arabirimi ve arabirimi kullanın.

  <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> Hizmetten bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> arayüz edinin.

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> Yöntemden <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> arabirimi edinin.

  Belirteç listesindeki değişiklikleri dinlemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> arabirimi uygulayın.

- Anahat Oluşturma

  Anahat oluşturmayı desteklemek için çeşitli seçenekler vardır. Örneğin, **Tanımlara Karşı Daralt** komutunu destekleyebilir, düzenleyici denetimli anahat bölgeleri sağlayabilir veya istemci denetimindeki bölgeleri destekleyebilirsiniz. Daha fazla bilgi için [bkz: Eski bir dil hizmetinde genişletilmiş anahat desteği sağlayın.](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

- Dil hizmeti kaydı

  Bir dil hizmetini nasıl kaydedin hakkında daha fazla [Manage VSPackages](../../extensibility/managing-vspackages.md)bilgi için [bkz.](../../extensibility/internals/registering-a-legacy-language-service2.md)

- İçeriğe duyarlı yardım

  Düzenleyiciye bağlamı aşağıdaki yollardan birinde sağlayın:

  - Arabirimi uygulayarak metin işaretçileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> için bağlam sağlayın.

  - Arabirimi uygulayarak tüm <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> kullanıcı bağlamını sağlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski bir dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
