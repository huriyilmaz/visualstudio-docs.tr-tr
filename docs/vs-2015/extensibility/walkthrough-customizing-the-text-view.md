---
title: 'İzlenecek yol: metin görünümünü özelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202019"
---
# <a name="walkthrough-customizing-the-text-view"></a>İzlenecek Yol: Metin Görünümünü Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir metin görünümünü, düzenleyici biçimindeki haritada aşağıdaki özelliklerden birini değiştirerek özelleştirebilirsiniz:  
  
- Gösterge kenar boşluğu  
  
- Ekleme giriş işareti  
  
- Giriş işaretinin üzerine yaz  
  
- Seçili metin  
  
- Etkin olmayan seçili metin (yani, odağa kayıp olan seçili metin)  
  
- Görünür boşluk  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `ViewPropertyTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="defining-the-content-type"></a>Içerik türünü tanımlama  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `ViewPropertyModifier` .  
  
2. Aşağıdaki yönergeleri ekleyin `using` :  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Öğesinden devralan adlı bir sınıf bildirin `TestViewCreationListener` <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Bu sınıfı aşağıdaki özniteliklerle dışarı aktarın:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Bu dinleyicinin uygulandığı içerik türünü belirtmek için.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Bu dinleyicinin rolünü belirtmek için.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Bu sınıfta, öğesini içe aktarın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Görünüm özelliklerini değiştirme  
  
1. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Görünümü açıldığında görünüm özelliklerinin değişmesi için yöntemini uygulayın. Değişikliği yapmak için önce <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümün yönüdür karşılık gelen öğesini bulun. Sonra kaynak sözlüğünde uygun özelliği değiştirin ve özellikleri ayarlayın. <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> Özelliklerini ayarlamadan önce yöntemini çağırarak ve sonra özellikleri ayarladıktan sonra yöntemine yapılan çağrıları toplu olarak ayarlayın <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> .  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
  
1. Çözümü derleyin.  
  
     Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
2. Bir metin dosyası oluşturun ve metin yazın.  
  
    - Ekleme giriş işareti Macenta olmalıdır ve üzerine yazma şapka karakteri turkuaz olmalıdır.  
  
    - Gösterge kenar boşluğu (metin görünümünün solunda) açık yeşil olmalıdır.  
  
3. Yeni yazdığınız metni seçin. Seçilen metnin rengi açık pembe olmalıdır.  
  
4. Metin seçiliyken metin penceresinin dışında herhangi bir yere tıklayın. Seçilen metnin rengi koyu pembe olmalıdır.  
  
5. Görünür boşluğu açın. ( **Düzenle** menüsünde **Gelişmiş** ' in üzerine gelin ve ardından **boşluğu görüntüle**' ye tıklayın. Metinde bazı Sekmeler yazın. Sekmeleri temsil eden kırmızı oklar görüntülenmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)
