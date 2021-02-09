---
title: Görselleştiricisi mimarisi | Microsoft Docs
description: Görselleştirici belirli bir veri öğesi türünü görüntüler ve ayrıca düzenlenmesine izin verebilir. Görselleştirici mimarisi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9df1dfa1912c54d30c5c428ec59de9432fe68051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884253"
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

 Hata ayıklayıcı tarafı kodu, veri Ipucu, Gözcü penceresi veya QuickWatch gibi hata ayıklayıcı arabiriminden çağrılabilecek kendi Kullanıcı arabirimini oluşturur. Görselleştiricisi arabirimi <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> sınıfı ve arabirimi kullanılarak oluşturulur <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> . Tüm Görselleştirici API 'Leri gibi, DialogDebuggerVisualizer ve ıdialogvisualizerhizmeti <xref:Microsoft.VisualStudio.DebuggerVisualizers> ad alanında bulunur.

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|

 Kullanıcı arabirimi, hata ayıklayıcı tarafında bulunan bir nesne sağlayıcısından görselleştirilebilen verileri alır:

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|
|Nesne sağlayıcısı (uygular <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> )||

 Hata ayıklanan tarafta nesne kaynağı olarak adlandırılan karşılık gelen bir nesne vardır:

|Hata ayıklayıcı tarafı|Hata ayıklanan kenar|
|-------------------|-------------------|
|DialogDebuggerVisualizer sınıfı<br /><br /> Idalogvisualizerservice arabirimi|Veri nesnesi|
|Nesne sağlayıcısı (uygular <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> )|Nesne kaynağı (türetilen <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> )|

 Nesne sağlayıcısı, görselleştiricisi Kullanıcı arabirimine görselleştirilebilen nesne verileri sağlar. Nesne sağlayıcısı nesne kaynağından nesne verilerini alır. Nesne sağlayıcısı ve nesne kaynağı, hata ayıklayıcı tarafı ve hata ayıklama tarafı arasındaki nesne verilerini iletmek için API 'Ler sağlar.

 Her Görselleştirici görselleştirilebilen veri nesnesini almalıdır. Aşağıdaki tabloda, nesne sağlayıcısının ve nesne kaynağının bu amaçla kullandığı ilgili API 'Ler gösterilmektedir:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Nesne sağlayıcısının veya kullanmasına dikkat edin <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> . API, nesne kaynağında çağrısına neden olur <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> . <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> <xref:System.IO.Stream?displayProperty=fullName> Görselleştirilebilen nesnenin seri hale getirilmiş formunu temsil eden, bir içinde doldurma çağrısı.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> daha sonra, ile oluşturduğunuz Kullanıcı arabiriminde görüntülenebilecek verileri nesne biçimine geri çıkarır <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> . <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> verileri ham olarak doldurur `Stream` , bu da kendi kendinize serisini kaldırmalısınız. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName><xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, serileştirilmiş ve `Stream` sonra verileri seri durumdan çıkarmak için çağırarak işe yarar. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>Nesne .NET tarafından serileştirilebilir olmadığında ve özel serileştirme gerektirdiğinde kullanın. Bu durumda, yöntemini de geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> .

 Salt okunurdur ve ile tek yönlü bir iletişim oluşturuyorsanız, <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> veya <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> yeterlidir. Veri nesnelerini düzenlemenizi destekleyen bir Görselleştirici oluşturuyorsanız, daha fazla yapmanız gerekir. Nesne sağlayıcısından bir veri nesnesini ayrıca nesne kaynağına geri gönderebilmelisiniz. Aşağıdaki tabloda, bu amaçla kullanılan nesne sağlayıcısı ve nesne kaynağı API 'Leri gösterilmektedir:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Bir kez, nesne sağlayıcısının kullanabileceği iki API olduğuna dikkat edin. Veri, nesne sağlayıcısından nesne kaynağına her zaman bir olarak gönderilir `Stream` , ancak <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> nesneyi kendi kendinize serileştirmek ister `Stream` .

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> sağladığınız bir nesneyi alır, bir öğesine dizir ve `Stream` sonra <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> öğesine göndermek için çağırır `Stream` <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> .

 Replace yöntemlerinden birinin kullanılması, hata ayıklanan içinde görselleştirilen nesnenin yerini alan yeni bir veri nesnesi oluşturur. Özgün nesnenin içeriğini değiştirmeden değiştirmek istiyorsanız, aşağıdaki tabloda gösterilen aktarım yöntemlerinden birini kullanın. Bu API 'Ler, görselleştirilebilen nesneyi değiştirmeden, verileri aynı anda her iki yönde de aktarır:

|Nesne sağlayıcısı|Nesne kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Görselleştirici güvenlik konuları](../debugger/visualizer-security-considerations.md)