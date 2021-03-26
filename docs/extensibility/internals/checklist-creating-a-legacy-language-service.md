---
title: 'Denetim listesi: eski dil hizmeti oluşturma | Microsoft Docs'
description: Visual Studio çekirdek Düzenleyicisi için eski dil hizmeti oluşturmak için gerçekleştirmeniz gereken temel adımları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111e72714f4afd56b7b53e9cc48329ba6ce68162
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074801"
---
# <a name="checklist-create-a-legacy-language-service"></a>Denetim listesi: eski dil hizmeti oluşturma
Aşağıdaki denetim listesi, çekirdek Düzenleyici için bir dil hizmeti oluşturmak üzere uygulamanız gereken temel adımları özetler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dil hizmetinizi ile tümleştirmek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir hata ayıklama ifade değerlendiricisi oluşturmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcısı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)IÇINDE [bir clr ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) .

## <a name="steps-to-create-a-language-service"></a>Dil hizmeti oluşturma adımları

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> arabirimini gerçekleştirin.

    - VSPackage 'da, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> dil hizmetini sağlamak için arabirimini uygulayın.

    - Dil hizmetinizi uygulamanızda tümleşik geliştirme ortamı (IDE) için kullanılabilir hale getirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> .

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Ana dil hizmeti sınıfında arabirimini uygulayın.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Arabirim, çekirdek Düzenleyici ve dil hizmeti arasındaki etkileşimin başlangıç noktasıdır.

### <a name="optional-features"></a>İsteğe bağlı özellikler
 Aşağıdaki özellikler isteğe bağlıdır ve herhangi bir sırada uygulanabilir. Bu özellikler dil hizmetinizin işlevlerini artırır.

- Sözdizimi renklendirme

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini gerçekleştirin. Bu arabirimin uygulamanız, uygun renk bilgilerini döndürmek için ayrıştırıcı bilgilerine sahip olmalıdır.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>Yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi döndürür. Her metin arabelleği için ayrı bir Colorizer örneği oluşturulur, bu nedenle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi ayrı olarak uygulamalısınız. Daha fazla bilgi için bkz. [eski dil hizmetindeki sözdizimi renklendirme](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Kod penceresi

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>Dil hizmetinin yeni bir kod penceresi oluşturulduğunda bildirim almasını sağlamak için arabirimini uygulayın.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>Yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> arabirimi döndürür. Dil hizmeti daha sonra, içindeki kod penceresine özel kullanıcı arabirimi ekleyebilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Dil hizmeti, içinde metin görünümü filtresi ekleme gibi özel bir işlem de yapabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Metin görünümü filtresi

  Bir dil hizmetinde IntelliSense ifadesinin tamamlanmasını sağlamak için, metin görünümünün daha sonra işleyeceği bazı komutlardan bazılarını ele almanız gerekir. Bu komutları ele almak için aşağıdaki adımları izleyin:

  - <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Komut zinciri ve tanıtıcı düzenleyici komutlarına katılmak için uygulayın.

  - Yöntemini çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> ve uygulamanızda geçiş yapın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

  - <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>Bu komutların artık size geçirilmemesi için görünümden ayrıldığınızda yöntemini çağırın.

  İşlenmesi gereken komutlar, sunulan hizmetlere göre değişir. Daha fazla bilgi için bkz. [dil hizmeti filtreleri Için önemli komutlar](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Arabirimin arabirimiyle aynı nesne üzerinde uygulanması gerekir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Ekstre tamamlama

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimini gerçekleştirin.

  Deyimin tamamlanma komutunu (yani, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) destekler ve arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> geçirerek arayüzde yöntemi çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> . Daha fazla bilgi için, bkz. [eski dil hizmetinde deyimin tamamlanması](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Yöntem ipuçları

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>Yöntem ipucu penceresi için veri sağlamak üzere arabirimini uygulayın.

  Komutları uygun şekilde işlemek için metin görünümü filtresini, bir yöntem veri ipucu penceresinin ne zaman gösterileceğini bilmeniz için yükleyebilirsiniz. Daha fazla bilgi için, [eski dil hizmetindeki parametre bilgilerine](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)bakın.

- Hata işaretçileri

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirimini gerçekleştirin.

  Arabirimi uygulayan hata işaretleyici nesneleri oluşturun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> hata işaretçisi nesnesinin arabirimini geçirerek yöntemi çağırın.

  Genellikle her bir hata işaretleyicisi, görev listesi penceresindeki bir öğeyi yönetir.

- Görev listesi öğeleri

  Arabirimi sağlayan bir görev öğesi sınıfı uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> .

  Arabirimini ve arabirimini sağlayan bir görev sağlayıcısı sınıfı uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> .

  Arabirimi sağlayan bir görev Numaralandırıcı sınıfı uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> .

  Görev sağlayıcısını görev listesinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> yöntemiyle kaydedin.

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>Hizmet GUID 'si ile dil hizmetinin hizmet sağlayıcısını çağırarak arabirimi edinin <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Görev öğesi nesneleri oluşturun ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> Yeni veya güncelleştirilmiş görevler olduğunda arabirimindeki yöntemi çağırın.

- Açıklama görevi öğeleri

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Açıklama görev belirteçlerini almak için arabirimini ve arabirimini kullanın.

  Hizmetten bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> arabirim edinin <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>Yönteminden arabirimini alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> .

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>Belirteç listesindeki değişiklikleri dinlemek için arabirimini uygulayın.

- Anahat Oluşturma

  Anahat oluşturmayı desteklemek için çeşitli seçenekler vardır. Örneğin, **tanımlara göre Daralt** komutunu destekleyebilir, düzenleyici denetimli ana hat bölgelerini sağlayabilir veya istemci denetimli bölgeleri destekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eski dil hizmetinde genişletilmiş ana hat desteği sağlama](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Dil hizmeti kaydı

  Dil hizmetinin nasıl kaydedileceği hakkında daha fazla bilgi için bkz. [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service2.md) ve [VSPackages yönetme](../../extensibility/managing-vspackages.md).

- Bağlama duyarlı yardım

  Aşağıdaki yollarla düzenleyiciye bağlam sağlayın:

  - Arabirimi uygulayarak metin işaretçileri için bağlam sağlayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .

  - Arabirimini uygulayarak tüm kullanıcı bağlamını sağlayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> .

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
