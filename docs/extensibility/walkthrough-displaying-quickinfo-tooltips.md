---
title: 'İzlenecek yol: QuickInfo araç Ipuçlarını görüntüleme | Microsoft Docs'
description: Bu yönergeyi kullanarak metin içeriği için hızlı bilgi görüntülemeyi öğrenin. QuickInfo bir yöntem adı için yöntem imzalarını ve açıklamalarını görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: d374aa41d85b1d64b6623cb99f6183787a2afc53
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217261"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>İzlenecek yol: hızlı bilgi araç ipuçlarını görüntüle
QuickInfo, Kullanıcı işaretçiyi bir yöntem adı üzerine taşırken Yöntem imzalarını ve açıklamalarını görüntüleyen bir IntelliSense özelliğidir. QuickInfo gibi dil tabanlı özellikleri, hızlı bilgi açıklamaları sağlamak istediğiniz tanımlayıcıları tanımlayarak ve sonra içeriğin görüntüleneceği bir araç ipucu oluşturmak için uygulayabilirsiniz. Hızlı bilgileri bir dil hizmeti bağlamında tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve yalnızca bu tür için hızlı bilgileri görüntüleyebilir veya var olan bir içerik türü için QuickInfo görüntüleyebilirsiniz (örneğin, "metin"). Bu izlenecek yol, "metin" içerik türü için hızlı bilgi görüntülemeyi gösterir.

 Bu kılavuzda QuickInfo örneği, bir kullanıcı işaretçiyi bir yöntem adı üzerine taşırken araç ipuçlarını görüntüler. Bu tasarım için şu dört arabirimi uygulamanız gerekir:

- kaynak arabirim

- kaynak sağlayıcı arabirimi

- Denetleyici Arabirimi

- denetleyici sağlayıcı arabirimi

  Kaynak ve denetleyici sağlayıcıları Managed Extensibility Framework (MEF) bileşen bölümleridir ve kaynak ve denetleyici sınıflarının dışarı aktarılmasından ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> araç ipucu metin arabelleğini oluşturan, ve gibi <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> hızlı bilgi oturumunu tetikleyen ' de hizmet ve aracıları içeri aktarmaktan sorumludur.

  Bu örnekte, QuickInfo kaynağı yöntem adlarının ve açıklamalarının sabit kodlanmış bir listesini kullanır, ancak tam uygulamalarda, dil hizmeti ve dil belgeleri bu içeriği sağlamaktan sorumludur.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, indirme merkezinden Visual Studio SDK 'yı yüklemeniz gerekmez. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `QuickInfoTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulama
 QuickInfo kaynağı tanımlayıcı kümesini ve açıklamalarını toplamaktan ve tanımlayıcılardan biri ile karşılaşıldığında araç ipucu metin arabelleğine içerik eklemeye sorumludur. Bu örnekte, tanımlayıcılar ve açıklamaları yalnızca kaynak oluşturucuya eklenir.

#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin ve adlandırın `TestQuickInfoSource` .

2. *Microsoft. VisualStudio. Language. IntelliSense* için bir başvuru ekleyin.

3. Aşağıdaki içeri aktarmaları ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> ve bunu adlandırın `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. QuickInfo kaynak sağlayıcısı, metin arabelleği ve bir yöntem adları ve yöntem imzaları kümesi için alanlar ekleyin. Bu örnekte, yöntem adları ve imzalar `TestQuickInfoSource` oluşturucuda başlatılır.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. QuickInfo kaynak sağlayıcısını ve metin arabelleğini ayarlayan bir Oluşturucu ekleyin ve yöntem adları kümesini ve Yöntem imzalarını ve açıklamalarını doldurur.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> . Bu örnekte, yöntemi geçerli sözcüğü ya da imleç bir satırın sonunda veya bir metin arabelleği ise, önceki sözcüğü bulur. Sözcük Yöntem adlarından biri ise, bu yöntem adının açıklaması QuickInfo içeriğine eklenir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. Şunları gerçekleştirdiğinden Dispose () yöntemini de uygulamalısınız <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulama
 QuickInfo kaynağının sağlayıcısı öncelikle kendisini bir MEF bileşeni parçası olarak dışa aktarıp QuickInfo kaynağını oluşturur. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilir.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Bir QuickInfo kaynak sağlayıcısı uygulamak için

1. Uygulayan adlı bir QuickInfo kaynak sağlayıcısı bildirin `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source", bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ile dışarı aktarın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. İki düzenleyici hizmetini <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , özellikleri olarak içeri aktarın `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>Yeni bir döndürecek şekilde uygulayın `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulama
 QuickInfo denetleyicileri hızlı bilgi görüntülendiğinde belirlenir. Bu örnekte, işaretçi Yöntem adlarından birine karşılık gelen bir sözcüğün üzerindeyken QuickInfo belirir. QuickInfo denetleyicisi, bir QuickInfo oturumunu tetikleyen bir fare üzerine gelme olay işleyicisi uygular.

### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulamak için

1. Uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> ve bunu adlandırın `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Metin görünümünde, hızlı bilgi oturumunda ve QuickInfo denetleyici sağlayıcısında temsil edilen metin arabellekleri için metin görünümü için özel alanlar ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Alanları ayarlayan ve fare üzerine gelme olay işleyicisini ekleyen bir Oluşturucu ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. QuickInfo oturumunu tetikleyen fare üzerine gelme olay işleyicisini ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>Denetleyici metin görünümünden ayrıldığında fare üzerine gelme olay işleyicisini kaldırabilmesi için yöntemini uygulayın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>Yöntemini ve <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> yöntemini Bu örnek için boş yöntemler olarak uygulayın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulama
 QuickInfo denetleyicisi sağlayıcısı öncelikle kendisini bir MEF bileşeni parçası olarak dışa aktarıp QuickInfo denetleyicisi örneğini oluşturur. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilir.

### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulamak için

1. Uygulayan adlı bir sınıf bildirin `TestQuickInfoControllerProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ile dışarı aktarın:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>Özelliği olarak içeri aktarın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>QuickInfo denetleyicisini örnekleyerek yöntemi uygulayın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için QuickInfoTest çözümünü derleyin ve deneysel örnekte çalıştırın.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve "Ekle" ve "çıkart" sözcüklerini içeren bir metin yazın.

4. İşaretçiyi "Ekle" oluşumlarından birinin üzerine taşıyın. İmza ve `add` yöntemin açıklaması görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
