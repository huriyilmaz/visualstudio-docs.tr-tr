---
title: 'İzlenecek yol: metin görünümünü özelleştirme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7a62ee2b55bf2b56ae1d8e28fc1910ed444c29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904929"
---
# <a name="walkthrough-customize-the-text-view"></a>İzlenecek yol: metin görünümünü özelleştirme
Bir metin görünümünü, düzenleyici biçimindeki haritada aşağıdaki özelliklerden birini değiştirerek özelleştirebilirsiniz:

- Gösterge kenar boşluğu

- Ekleme giriş işareti

- Giriş işaretinin üzerine yaz

- Seçili metin

- Etkin olmayan seçili metin (yani, odak kaybolan seçili metin)

- Görünür boşluk

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `ViewPropertyTest` .

2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin ve adlandırın `ViewPropertyModifier` .

2. Aşağıdaki yönergeleri ekleyin `using` :

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Öğesinden devralan adlı bir sınıf bildirin `TestViewCreationListener` <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Bu sınıfı aşağıdaki özniteliklerle dışarı aktarın:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Bu dinleyicinin uygulandığı içerik türünü belirtmek için.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Bu dinleyicinin rolünü belirtmek için.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. Bu sınıfta, öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Görünüm özelliklerini değiştirme

1. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Yöntemi, görünüm açıldığında görünüm özelliklerinin değişmesi için ayarlayın. Değişikliği yapmak için önce <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümün yönüdür karşılık gelen öğesini bulun. Ardından, kaynak sözlüğünde uygun özelliği değiştirin ve özellikleri ayarlayın. <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> Özelliklerini ayarlamadan önce yöntemini çağırarak ve sonra özellikleri ayarladıktan sonra yöntemine yapılan çağrıları toplu olarak ayarlayın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> .

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin

1. Çözümü derleyin.

     Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

2. Bir metin dosyası oluşturun ve metin yazın.

    - Ekleme giriş işareti Macenta olmalıdır ve üzerine yazma şapka karakteri turkuaz olmalıdır.

    - Gösterge kenar boşluğu (metin görünümünün solunda) açık yeşil olmalıdır.

3. Yazdığınız metni seçin. Seçilen metnin rengi açık pembe olmalıdır.

4. Metin seçiliyken metin penceresinin dışında herhangi bir yere tıklayın. Seçilen metnin rengi koyu pembe olmalıdır.

5. Görünür boşluğu açın. ( **Düzenle** menüsünde **Gelişmiş** ' in üzerine gelin ve ardından **boşluğu görüntüle**' ye tıklayın. Metinde bazı Sekmeler yazın. Sekmeleri temsil eden kırmızı oklar görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
