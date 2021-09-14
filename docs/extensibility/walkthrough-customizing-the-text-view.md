---
title: 'İzlenecek yol: metin görünümünü özelleştirme | Microsoft Docs'
description: Bu kılavuzu kullanarak, düzenleyici biçimindeki haritada birkaç özelliği değiştirerek bir metin görünümünü özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fd60c6e9c6253a214de7a08173462895cdf29fc1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628845"
---
# <a name="walkthrough-customize-the-text-view"></a>İzlenecek yol: metin görünümünü özelleştirme
Bir metin görünümünü, düzenleyici biçimindeki haritada aşağıdaki özelliklerden birini değiştirerek özelleştirebilirsiniz:

- Gösterge kenar boşluğu

- Ekleme giriş işareti

- Giriş işaretinin üzerine yaz

- Seçili metin

- Etkin olmayan seçili metin (yani, odak kaybolan seçili metin)

- Görünür boşluk

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSıX projesi oluşturun. ( **yeni Project** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **vsıx Project**' i seçin.) Çözümü adlandırın `ViewPropertyTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin ve adlandırın `ViewPropertyModifier` .

2. Aşağıdaki yönergeleri ekleyin `using` :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Öğesinden devralan adlı bir sınıf bildirin `TestViewCreationListener` <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Bu sınıfı aşağıdaki özniteliklerle dışarı aktarın:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Bu dinleyicinin uygulandığı içerik türünü belirtmek için.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Bu dinleyicinin rolünü belirtmek için.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. Bu sınıfta, öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Görünüm özelliklerini değiştirme

1. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Yöntemi, görünüm açıldığında görünüm özelliklerinin değişmesi için ayarlayın. Değişikliği yapmak için önce <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümün yönüdür karşılık gelen öğesini bulun. Ardından, kaynak sözlüğünde uygun özelliği değiştirin ve özellikleri ayarlayın. <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> Özelliklerini ayarlamadan önce yöntemini çağırarak ve sonra özellikleri ayarladıktan sonra yöntemine yapılan çağrıları toplu olarak ayarlayın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin

1. Çözümü derleyin.

     bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio ikinci bir örneği başlatılır.

2. Bir metin dosyası oluşturun ve metin yazın.

    - Ekleme giriş işareti Macenta olmalıdır ve üzerine yazma şapka karakteri turkuaz olmalıdır.

    - Gösterge kenar boşluğu (metin görünümünün solunda) açık yeşil olmalıdır.

3. Yazdığınız metni seçin. Seçilen metnin rengi açık pembe olmalıdır.

4. Metin seçiliyken metin penceresinin dışında herhangi bir yere tıklayın. Seçilen metnin rengi koyu pembe olmalıdır.

5. Görünür boşluğu açın. ( **Düzenle** menüsünde **Gelişmiş** ' in üzerine gelin ve ardından **boşluğu görüntüle**' ye tıklayın. Metinde bazı Sekmeler yazın. Sekmeleri temsil eden kırmızı oklar görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
