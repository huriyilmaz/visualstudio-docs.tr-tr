---
title: 'İzlenme: Metin Görünümünü Özelleştirme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697462"
---
# <a name="walkthrough-customize-the-text-view"></a>İzlenme: Metin görünümünü özelleştirme
Editör biçimindeki haritasında aşağıdaki özelliklerden herhangi birini değiştirerek metin görünümünü özelleştirebilirsiniz:

- Gösterge marjı

- Ekleme bakıcısı

- Overwrite caret

- Seçili metin

- Etkin olmayan seçili metin (diğer bir deyişle, odağı kaybolan seçili metin)

- Görünür beyaz boşluk

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `ViewPropertyTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin `ViewPropertyModifier`ve adlandırın.

2. Aşağıdaki `using` yönergeleri ekleyin:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. 'den `TestViewCreationListener` <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>devralınan adlandırılmış bir sınıf bildirin Bu sınıfı aşağıdaki özniteliklerle dışa aktar:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>bu dinleyicinin uyguladığı içerik türünü belirtmek için.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>bu dinleyicinin rolünü belirtmek için.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. Bu sınıfta, 'yi. <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Görünüm özelliklerini değiştirme

1. Görünüm açıldığında <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> görünüm özelliklerinin değiştirilen şekilde yöntemi ayarlayın. Değişikliği yapmak için, önce <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümün yönüne karşılık gelen bu bulguyu bulun. Ardından, kaynak sözlüğündeki uygun özelliği değiştirin ve özellikleri ayarlayın. Özellikleri ayarlamadan <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> önce <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> yöntemi arayarak ve sonra da <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> özellikleri ayarladıktan sonra metodun çağrılarını toplu olarak tamamlayın.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin

1. Çözümü derleyin.

     Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

2. Bir metin dosyası oluşturun ve bazı metin yazın.

    - Ekleme caret macenta olmalı ve üzerine yazılan caret turkuaz olmalıdır.

    - Gösterge kenar boşluğu (metin görünümünün solunda) açık yeşil olmalıdır.

3. Yazdığınız metni seçin. Seçili metnin rengi açık pembe olmalıdır.

4. Metin seçiliyken, metin penceresinin dışında herhangi bir yeri tıklatın. Seçili metnin rengi koyu pembe olmalıdır.

5. Görünür beyaz boşluğu açın. **(Edit** menüsünde **Gelişmiş'i** işaret edin ve ardından **Beyaz Uzayı Görüntüle'yi**tıklatın). Metne bazı sekmeler yazın. Sekmeleri temsil eden kırmızı oklar görüntülenmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
