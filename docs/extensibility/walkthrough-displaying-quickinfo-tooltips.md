---
title: 'adım adım kılavuz: HızlıBilgi Araç İpucu | Microsoft Docs'
description: Bu izlenecek yolu kullanarak metin içeriği için QuickInfo görüntülemeyi öğrenin. QuickInfo, yöntem adı için yöntem imzalarını ve açıklamalarını görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6039f8a3bbdc2f2263886486b3be17ec3e0b5053
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049057"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Adım adım kılavuz: QuickInfo araç ipucu görüntüleme
QuickInfo, bir kullanıcı işaretçiyi yöntem adının üzerine taşırken yöntem imzalarını ve açıklamalarını görüntüleyen bir IntelliSense özelliğidir. QuickInfo gibi dil tabanlı özellikleri, QuickInfo açıklamalarını sağlamak istediğiniz tanımlayıcıları tanımlayarak ve ardından içeriği görüntülemek için bir araç ipucu oluşturarak gerçekleştirebilirsiniz. QuickInfo'ları bir dil hizmeti bağlamında tanımlayabilir veya kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve QuickInfo'ya yalnızca bu tür için veya mevcut içerik türü için QuickInfo'ya ("metin" gibi) bakabilirsiniz. Bu kılavuzda , "metin" içerik türü için QuickInfo'ya nasıl ulaşabilirsiniz?

 Bu kılavuzda QuickInfo örneği, bir kullanıcı işaretçiyi yöntem adının üzerine taşırken araç ipucu görüntüler. Bu tasarım için şu dört arabirimi uygulama gerekir:

- kaynak arabirimi

- kaynak sağlayıcı arabirimi

- denetleyici arabirimi

- denetleyici sağlayıcısı arabirimi

  Kaynak ve denetleyici sağlayıcıları Managed Extensibility Framework (MEF) bileşen parçalarıdır ve kaynak ve denetleyici sınıflarını dışarı aktarmanın yanı sıra araç ipucu metin arabelleği oluşturan ve QuickInfo oturumunu tetikleyen gibi hizmet ve aracıları içeri aktarmadan <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> sorumludur.

  Bu örnekte, QuickInfo kaynağı yöntem adlarının ve açıklamalarının sabit kodlu bir listesini kullanır, ancak tam uygulamalarda dil hizmeti ve dil belgeleri bu içeriği sağlamakla sorumludur.

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, indirme merkezinden Visual Studio SDK'sı yüklemenize gerek yoktur. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. C# VSIX projesi oluşturun. (Yeni **Project** iletişim kutusunda **Visual C# / Genişletilebilirlik'i** seçin, ardından **VSIX Project**.) Çözüme adını `QuickInfoTest` girin.

2. Projeye bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

## <a name="implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulama
 Tanımlayıcıların ve açıklamalarının kümelerini toplamak ve tanımlayıcılardan biri ile karşılaşıldıklarında içeriği araç ipucu metin arabelleğine eklemek QuickInfo kaynağından sorumludur. Bu örnekte tanımlayıcılar ve açıklamaları kaynak oluşturucuya eklenir.

#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo kaynağını uygulamak için

1. Bir sınıf dosyası ekleyin ve olarak ad `TestQuickInfoSource` girin.

2. *Microsoft.VisualStudio.Language.IntelliSense'e başvuru ekleyin.*

3. Aşağıdaki içeri aktarmaları ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> ve olarak ad `TestQuickInfoSource` girin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. QuickInfo kaynak sağlayıcısı, metin arabelleği ve yöntem adları ile yöntem imzaları kümesi için alanlar ekleyin. Bu örnekte, yöntem adları ve imzaları oluşturucuda `TestQuickInfoSource` başlatılır.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. QuickInfo kaynak sağlayıcısını ve metin arabelleğini ayar alan ve yöntem adları ile yöntem imzaları ile açıklamaları kümelerini doldurmak için bir oluşturucu ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> uygulama. Bu örnekte yöntemi, geçerli sözcüğü veya imleç bir satırın veya metin arabelleğinin sonunda yer alırsa önceki sözcüğü bulur. Sözcük yöntem adlarından biri ise, bu yöntem adının açıklaması QuickInfo içeriğine eklenir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. uygulayan bir Dispose() yöntemi de <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable> uygulamalısiniz:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulama
 QuickInfo kaynağının sağlayıcısı öncelikle kendisini MEF bileşeni olarak dışarı aktarmaya ve QuickInfo kaynağının örneğini oluşturmaya hizmet eder. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilirsiniz.

#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo kaynak sağlayıcısı uygulamak için

1. uygulayan adlı bir QuickInfo kaynak sağlayıcısını bildirin ve `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before="default" değeri ve "text" değeriyle dışarı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> aktarın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. özellikleri olarak iki düzenleyici hizmeti <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> (ve ) içeri `TestQuickInfoSourceProvider` aktarın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Yeni <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> bir dönmek için `TestQuickInfoSource` uygulama.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulama
 QuickInfo denetleyicileri, QuickInfo'nın ne zaman görüntülendiğinden belirler. Bu örnekte, işaretçi yöntem adlarından birini karşılık gelen bir sözcük üzerinde olduğunda QuickInfo görünür. QuickInfo denetleyicisi, bir QuickInfo oturumunu tetikleyen fareyle üzerine gelindiğinde olay işleyicisi kullanır.

### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo denetleyicisi uygulamak için

1. uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> ve olarak ad `TestQuickInfoController` girin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Metin görünümü, metin görünümünde temsil edilen metin arabellekleri, QuickInfo oturumu ve QuickInfo denetleyici sağlayıcısı için özel alanlar ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Alanları ayarleyen ve fareyle üzerine gelinen olay işleyicisini ekleyen bir oluşturucu ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. QuickInfo oturumunu tetikleyen fareyle üzerine gelme olay işleyicisini ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Denetleyici metin görünümünden ayrılarak fareyle üzerine gelindiğinde olay işleyicisini <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> kaldıran yöntemini uygulama.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> ve yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> bu örnek için boş yöntemler olarak uygulama.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulama
 QuickInfo denetleyicisinin sağlayıcısı öncelikle kendisini BIR MEF bileşeni parçası olarak dışarı aktarmaya ve QuickInfo denetleyicisinin örneğini oluşturmaya hizmet eder. Bir MEF bileşeni parçası olduğundan, diğer MEF bileşen parçalarını içeri aktarabilirsiniz.

### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo denetleyici sağlayıcısını uygulamak için

1. uygulayan adlı bir sınıf bildirin ve `TestQuickInfoControllerProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" ve "text" ile dışarı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> aktarın:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. özelliğini <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> bir özellik olarak içeri aktarın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>QuickInfo denetleyicisini başlatarak yöntemini uygulama.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Kodu derleme ve test
 Bu kodu test etmek için QuickInfoTest çözümünü derleme ve deneysel örnekte çalıştırma.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcısında çalıştırarak ikinci bir Visual Studio başlat.

3. Bir metin dosyası oluşturun ve "ekle" ve "çıkar" sözcüklerini içeren bazı metinler yazın.

4. İşaretçiyi "add" oluşumlarından birinin üzerine sürükleyin. Yöntemin imzası ve `add` açıklaması görüntüleniyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: İçerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
