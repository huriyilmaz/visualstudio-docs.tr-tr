---
title: 'Nasıl yapılır: Görselleştirici Yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833357"
---
# <a name="how-to-write-a-visualizer"></a>Nasıl Yapılır: Görselleştirici Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veya hariç olmak üzere, herhangi bir yönetilen sınıfın nesnesi için özel bir Görselleştirici <xref:System.Object> yazabilirsiniz <xref:System.Array> .  
  
> [!NOTE]
> **Mağaza** uygulamalarında yalnızca standart metın, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.  
  
 Bir hata ayıklayıcı görselleştiricisi mimarisi iki bölümden oluşur:  
  
- *Hata ayıklayıcı tarafı* Visual Studio hata ayıklayıcısı içinde çalışır. Hata ayıklayıcı tarafı kodu, görselleştiriciniz için Kullanıcı arabirimini oluşturur ve görüntüler.  
  
- Hata *ayıklanan yan* Işlem Visual Studio 'da çalışıyor (hata *ayıklanan*).  
  
  Görselleştirmek istediğiniz veri nesnesi (örneğin, bir String nesnesi) debugayıklanan süreçte bulunur. Bu nedenle, hata ayıklanan tarafın bu veri nesnesini hata ayıklayıcı tarafına gönderebilmesi gerekir, bu, daha sonra oluşturduğunuz bir kullanıcı arabirimini kullanarak görüntüleyebilir.  
  
  Hata ayıklayıcı tarafı, arabirimini uygulayan bir *nesne sağlayıcısından* görselleştirilebilen bu veri nesnesini alır <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . Hata ayıklanan yüz, veri nesnesini öğesinden türetilen *nesne kaynağı*üzerinden gönderir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Nesne sağlayıcısı Ayrıca verileri nesne kaynağına geri gönderebilir ve bu sayede, verileri görüntüleyen bir Görselleştirici de yazdırabilirsiniz. Nesne sağlayıcısı, ifade değerlendiricisi ile konuşmak için geçersiz kılınabilir ve bu nedenle nesne kaynağına  
  
  Hata ayıklanan yan ve hata ayıklayıcı tarafı ile bir birbirleriyle iletişim kurar <xref:System.IO.Stream> . Yöntemler bir veri nesnesini bir öğesine seri hale getirmek <xref:System.IO.Stream> ve <xref:System.IO.Stream> veri nesnesine geri dönmek için verilmiştir.  
  
  Hata ayıklanan taraf kodu DebuggerVisualizer özniteliği () kullanılarak belirtilir <xref:System.Diagnostics.DebuggerVisualizerAttribute> .  
  
  Hata ayıklayıcı tarafında görselleştiricisi Kullanıcı arabirimini oluşturmak için, öğesinden devralan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> arabirimi göstermek için yöntemi geçersiz kılmalısınız.  
  
  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>Görselleştiricinizden Windows Forms, iletişim kutuları ve denetimleri göstermek için kullanabilirsiniz.  
  
  Genel türler için destek sınırlıdır. Genel tür olan bir hedef için bir Görselleştirici yazarak, genel tür açık bir tür olur. Bu kısıtlama, özniteliği kullanılırken kısıtlama ile aynıdır `DebuggerTypeProxy` . Ayrıntılar için bkz. [DebuggerTypeProxy özniteliğini kullanma](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Özel görselleştiricilerin güvenlik konuları olabilir. Bkz. [Görselleştirici güvenlik konuları](../debugger/visualizer-security-considerations.md).  
  
  Aşağıdaki yordamlar, Görselleştirici oluşturmak için yapmanız gerekenler hakkında üst düzey bir görünüm sağlar. Daha ayrıntılı bir açıklama için bkz. [Izlenecek yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Hata ayıklayıcı tarafını oluşturmak için  
  
1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>Hata ayıklayıcı tarafında görselleştirilen nesneyi almak için yöntemleri kullanın.  
  
2. Öğesinden devralan bir sınıf oluşturun <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .  
  
3. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>Arabiriminizi göstermek için yöntemini geçersiz kılın. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>Windows Forms, iletişim kutuları ve denetimleri arayüzün bir parçası olarak göstermek için yöntemler kullanın.  
  
4. <xref:System.Diagnostics.DebuggerVisualizerAttribute>, Bir Görselleştirici () vererek uygulayın <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .  
  
### <a name="to-create-the-debuggee-side"></a>Hata ayıklanan tarafı oluşturmak için  
  
1. <xref:System.Diagnostics.DebuggerVisualizerAttribute>Bir Görselleştirici ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ) ve bir nesne kaynağı () vererek uygulayın <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Nesne kaynağını atlarsanız, varsayılan bir nesne kaynağı kullanılacaktır  
  
2. Görselin veri nesnelerini düzenleyebilmesini ve bunları görüntülemesini istiyorsanız, veya yöntemlerini geçersiz kılmanız gerekir `TransferData` `CreateReplacementObject` <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)   
 [Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Görselleştirici Güvenlik Konuları](../debugger/visualizer-security-considerations.md)
