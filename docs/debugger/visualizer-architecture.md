---
title: Görselleştiricisi mimarisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c92723a1b6abb371b44f1793f9ea5b1f8ad3bca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728472"
---
# <a name="visualizer-architecture"></a>Görselleştirici Mimarisi
Bir hata ayıklayıcı görselleştiricisi mimarisi iki bölümden oluşur:

- *Hata ayıklayıcı tarafı* Visual Studio hata ayıklayıcısı içinde çalışır. Hata ayıklayıcı tarafı kodu, görselleştiriciniz için Kullanıcı arabirimini oluşturur ve görüntüler.

- Hata *ayıklanan yan* Işlem Visual Studio 'da çalışıyor (hata *ayıklanan*).

  Görselleştirici, hata ayıklayıcının bir veri nesnesinin içeriğini anlamlı, anlaşılır bir biçimde görüntülemesini (*görselleştirmesini*) sağlayan bir hata ayıklayıcı bileşenidir. Bazı Görselleştiriciler veri nesnesini de düzenlemenizi destekler. Özel Görselleştiriciler yazarak, hata ayıklayıcıyı kendi özel veri türlerinizi işleyecek şekilde genişletebilirsiniz.

  Görselleştirilebilen veri nesnesi hata ayıkladığınız işlem içinde (hata *ayıklanan* işlem) bulunuyor. Verileri görüntüleyen kullanıcı arabirimi, Visual Studio hata ayıklayıcı işlemi içinde oluşturulur:

|Hata ayıklayıcı Işlemi|Hata ayıklanan Işlem|
|----------------------|----------------------|
|Hata ayıklayıcı kullanıcı arabirimi (DataTips, Gözcü penceresi, hızlı Izleme)|Görselleştirilebilen veri nesnesi|

 Hata ayıklayıcı arabirimindeki veri nesnesini görselleştirmek için, iki işlem arasında iletişim kurmak üzere koda ihtiyacınız vardır. Sonuç olarak, görselleştiricisi mimarisi iki bölümden oluşur: *hata ayıklayıcı tarafı* kodu ve hata *ayıklanan yüz* kodu.

 Hata ayıklayıcı tarafı kodu, veri Ipucu, Gözcü penceresi veya QuickWatch gibi hata ayıklayıcı arabiriminden çağrılabilecek kendi Kullanıcı arabirimini oluşturur. Görselleştiricisi arabirimi <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> sınıfı ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> arabirimi kullanılarak oluşturulur. Tüm Görselleştirici API 'Leri gibi <xref:Microsoft.VisualStudio.DebuggerVisualizers> ad alanında DialogDebuggerVisualizer ve ıdialogvisualizerhizmeti bulunur.

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|

 Kullanıcı arabirimi, hata ayıklayıcı tarafında bulunan bir nesne sağlayıcısından görselleştirilebilen verileri alır:

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|
|Nesne sağlayıcısı (<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> uygular)||

 Hata ayıklanan tarafta nesne kaynağı olarak adlandırılan karşılık gelen bir nesne vardır:

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|
|Nesne sağlayıcısı (<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> uygular)|Nesne kaynağı (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> türetilir)|

 Nesne sağlayıcısı, görselleştiricisi Kullanıcı arabirimine görselleştirilebilen nesne verileri sağlar. Nesne sağlayıcısı nesne kaynağından nesne verilerini alır. Nesne sağlayıcısı ve nesne kaynağı, hata ayıklayıcı tarafı ve hata ayıklama tarafı arasındaki nesne verilerini iletmek için API 'Ler sağlar.

 Her Görselleştirici görselleştirilebilen veri nesnesini almalıdır. Aşağıdaki tabloda, nesne sağlayıcısının ve nesne kaynağının bu amaçla kullandığı ilgili API 'Ler gösterilmektedir:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Nesne sağlayıcısının <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> ya da <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> kullanmasına dikkat edin. API, nesne kaynağında <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> çağrısıyla sonuçlanır. Bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> çağrısı, görselleştirilen nesnenin serileştirilmiş formunu temsil eden bir <xref:System.IO.Stream?displayProperty=fullName> doldurur.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName>, verileri daha sonra <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ile oluşturduğunuz Kullanıcı arabiriminde görüntüleyebilen nesne formuna geri alabilir. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, verileri ham `Stream` olarak doldurur ve bu, kendi kendinize serisini kaldırmalısınız. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName>, serileştirilmiş `Stream` almak ve sonra verilerin serisini çıkarmak için <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> çağırarak işe yarar. Nesne .NET tarafından seri hale getirilmediğinden ve özel serileştirme gerektirdiğinde <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> kullanın. Bu durumda, <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> yöntemini de geçersiz kılmanız gerekir.

 Salt okunurdur, <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> veya <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> ile tek yönlü iletişim yeterlidir. Veri nesnelerini düzenlemenizi destekleyen bir Görselleştirici oluşturuyorsanız, daha fazla yapmanız gerekir. Nesne sağlayıcısından bir veri nesnesini ayrıca nesne kaynağına geri gönderebilmelisiniz. Aşağıdaki tabloda, bu amaçla kullanılan nesne sağlayıcısı ve nesne kaynağı API 'Leri gösterilmektedir:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Bir kez, nesne sağlayıcısının kullanabileceği iki API olduğuna dikkat edin. Veri, nesne sağlayıcısından `Stream` olarak nesne kaynağına gönderilir, ancak <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> nesneyi `Stream` kendi kendinize serileştirmek ister.

 sağladığınız bir nesneyi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>, bir `Stream` seri hale getirir ve sonra <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> `Stream` göndermek <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> çağırır.

 Replace yöntemlerinden birinin kullanılması, hata ayıklanan içinde görselleştirilen nesnenin yerini alan yeni bir veri nesnesi oluşturur. Özgün nesnenin içeriğini değiştirmeden değiştirmek istiyorsanız, aşağıdaki tabloda gösterilen aktarım yöntemlerinden birini kullanın. Bu API 'Ler, görselleştirilebilen nesneyi değiştirmeden, verileri aynı anda her iki yönde de aktarır:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Görselleştirici Yazma](/visualstudio/debugger/create-custom-visualizers-of-data)
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Görselleştirici Güvenlik Konuları](../debugger/visualizer-security-considerations.md)