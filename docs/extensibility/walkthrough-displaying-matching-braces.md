---
title: 'İzlenecek yol: eşleşen ayraçları görüntüleme | Microsoft Docs'
description: Bu kılavuzu kullanarak, metin içeriği türüne parantez ile eşleşen Etiketler uygulayarak bir dilin bağlamında küme ayraçları tanımlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dacf3ffff56580e445f2eeda851d30082ba90f45
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049148"
---
# <a name="walkthrough-display-matching-braces"></a>İzlenecek yol: eşleşen ayraçları görüntüle
Eşleştirmek istediğiniz küme ayraçlarını tanımlayarak, parantez eşleştirme ile eşleşen dil tabanlı özellikleri uygulayın ve şapka işareti ayraçlarından birinde olduğunda, eşleşen ayraçların içine bir metin işaretçisi etiketi ekleyin. Bir dilin bağlamında küme ayraçları tanımlayabilir, kendi dosya adı uzantınızı ve içerik türünü tanımlayabilir ve etiketleri yalnızca o türe uygulayabilir ya da etiketleri varolan bir içerik türüne (örneğin "metin") uygulayabilirsiniz. Aşağıdaki izlenecek yol, "metin" içerik türüne parantez ile eşleşen etiketlerin nasıl uygulanacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için

1. Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözümü adlandırın `BraceMatchingTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="implement-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulama
 Visual Studio kullanılan bir küme ayracı vurgulama efektini almak için, türünde bir tagger uygulayabilirsiniz <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Aşağıdaki kod, herhangi bir iç içe geçme düzeyinde küme ayracı çiftleri için etiketi nasıl tanımlayacağınızı gösterir. Bu örnekte, [] öğesinin küme ayracı çiftleri ve {} Tagger oluşturucusunda tanımlanmıştır, ancak tam dil uygulamasında, ilgili ayraç çiftleri dil belirtiminde tanımlanmıştır.

### <a name="to-implement-a-brace-matching-tagger"></a>Tagger ile eşleşen bir küme ayracı uygulamak için

1. Bir sınıf dosyası ekleyin ve Braceeþleþen olarak adlandırın.

2. Aşağıdaki ad alanlarını içeri aktarın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. Türünden devralan bir sınıf tanımlayın `BraceMatchingTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Metin görünümü, kaynak arabelleği, geçerli anlık görüntü noktası ve ayrıca küme ayracı çiftleri için özellikler ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. Tagger kurucusunda özellikleri ayarlayın ve görünüm değiştirme olayları ' na abone olun <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . Bu örnekte, tanım amaçları için, eşleşen çiftler oluşturucuda da tanımlanmıştır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. Uygulamanın bir parçası olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , TagsChanged olayını bildirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. Olay işleyicileri, özelliğin geçerli giriş işareti konumunu güncelleştirir `CurrentChar` ve TagsChanged olayını yükseltir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>Geçerli karakter açık bir küme ayracı olduğunda veya önceki karakter Visual Studio gibi bir kapanış ayracı olduğunda, küme ayraçlarını eşleştirmek için yöntemini uygulayın. Eşleşme bulunduğunda bu yöntem, biri açık küme ayracı ve diğeri de kapatma ayracı için olmak üzere iki etiket oluşturur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. Aşağıdaki özel yöntemler, eşleşen küme ayracını herhangi bir iç içe geçme düzeyinde bulur. İlk yöntem, açma karakteriyle eşleşen kapatma karakterini bulur:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. Aşağıdaki yardımcı yöntemi bir kapatma karakteriyle eşleşen açma karakterini bulur:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Bir ayraç ile eşleşen Tagger sağlayıcısı uygulama
 Bir Tagger uygulamaya ek olarak, bir Tagger sağlayıcısı da uygulamanız ve dışarı aktarmanız gerekir. Bu durumda, sağlayıcının içerik türü "metin" olur. Bu nedenle, parantez eşleştirme tüm metin dosyası türlerinde görünür, ancak Fuller bir uygulama yalnızca belirli bir içerik türüne sahip küme ayracı uygular.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Bir küme ayracı ile eşleşen Tagger sağlayıcısı uygulamak için

1. Öğesinden devralan bir Tagger sağlayıcısı bildirin <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , bu dosyayı BraceMatchingTaggerProvider olarak adlandırın ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ve a ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>Bir BraceMatchingTagger örneği oluşturmak için yöntemini uygulayın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, BraceMatchingTest çözümünü derleyin ve deneysel örnekte çalıştırın.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve eşleşen küme ayraçları içeren bir metin yazın.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Giriş işaretini bir açık küme ayracından önce konumlandırdığınızda, hem bu küme ayracı hem de eşleşen kapatma ayracı vurgulanmalıdır. İmleci kapalı küme ayracından hemen sonra konumlandırdığınızda, bu küme ayracı ve eşleşen açma ayracı her ikisi de vurgulanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
