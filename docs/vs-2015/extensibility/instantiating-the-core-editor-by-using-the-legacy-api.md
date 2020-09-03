---
title: Eski API 'YI kullanarak çekirdek düzenleyiciyi örnekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203916"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Temel Düzenleyiciyi Başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici, ekleme, silme, kopyalama ve yapıştırma gibi metin düzenleme işlevlerinden sorumludur. Bu işlevleri, metin renklendirme, girintileme ve IntelliSense bildiri tamamlama gibi dil Hizmetleri tarafından sağlananlarla birleştirir.  
  
 Temel düzenleyicinin bir örneğini üç şekilde örnekleyebilirsiniz:  
  
- Bir pencerede temel düzenleyicinin bir örneğini açık olarak oluşturun.  
  
- Çekirdek düzenleyicinin bir örneğini döndüren bir düzenleyici fabrikası sağlayın  
  
- Proje hiyerarşisinden bir dosya açın.  
  
  Aşağıdaki bölümlerde, Düzenleyiciyi başlatmak için eski API 'nin nasıl kullanılacağı ele alınmaktadır.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Bir çekirdek Düzenleyici örneğini açık olarak açma  
 Çekirdek düzenleyicinin bir örneğini açık olarak alırken:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>Düzenlenmekte olan belge verileri nesnesini tutmak için bir edinin.  
  
- Arabirimden bir arabirim oluşturarak belge verileri nesnesinin çizgi odaklı bir temsilini oluşturun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Yöntemi kullanılarak, arabirimin varsayılan uygulamasının bir örneği için belge veri nesnesi olarak ayarlayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> .  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>Yöntemini kullanarak örneği bir arabirimde barındırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> .  
  
  Bu noktada, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> arabirimini görüntülemek çekirdek düzenleyicinin bir örneğini içeren bir pencere sağlar.  
  
  Ancak, bu çok faydalı bir örnek değildir, çünkü kısayol tuşları yoktur ya da gelişmiş özelliklere erişin. Kısayol tuşlarına ve gelişmiş özelliklere erişim sağlamak için:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>Bir dil hizmetini ve düzenleyicinin kullandığı belge veri nesnesini ilişkilendirmek için yöntemini kullanın.  
  
- Kendi kısayol anahtarlarınızı oluşturun ya da nesnelerin görüntüleme özelliklerini ayarlayarak sistem varsayılanını kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> . Bunu yapmak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> özelliği ile yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
   Standart olmayan kısayol tuşlarını almak ve kullanmak için,. vsct dosyasını kullanarak bunları oluşturun. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Temel düzenleyiciyi almak için bir düzenleyici fabrikası kullanma  
 Yöntemini kullanarak bir düzenleyici fabrikası ile çekirdek Düzenleyici uygularken, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> nesne içindeki bir belge veri nesnesini kullanarak açıkça barındırmak için önceki bölümde özetlenen tüm adımları izleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> .  
  
 Metni göstermek için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesnesinden bir arabirim edinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi çağırın.  
  
 Düzenleyiciye bir dil hizmeti sağlamak için yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> içindeki yöntemi çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  
  
 Önceki bölümün aksine, varsayılan kısayol tuşlarını almak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yönteminden çekirdek düzenleyiciyi alırken yöntemi tarafından döndürülen komut bağlamını kullanırsınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  
  
 Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metin düzenleyicisiyle aynı komut GUID 'ini döndürürse, çekirdek düzenleyicinin örneği varsayılan kısayol tuşlarını otomatik olarak alır.  
  
 Genel bilgiler için bkz. [Izlenecek yol: Çekirdek Düzenleyici oluşturma ve bir düzenleyici dosya türünü kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek düzenleyicinin içinde](../extensibility/inside-the-core-editor.md)   
 [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)   
 [İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
