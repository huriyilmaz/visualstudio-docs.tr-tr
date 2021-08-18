---
title: Görselleştirici Mimarisi | Microsoft Docs
description: Görselleştirici belirli bir veri öğesi türünü görüntüler ve düzenlemeye de izin veli olabilir. Görselleştiricinin mimarisi hakkında bilgi edinmek.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3def27cc4960852bce00fdc65f575231c9be871f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161004"
---
# <a name="visualizer-architecture"></a>Görselleştirici Mimarisi
Hata ayıklayıcı görselleştiricisi mimarisinin iki bölümü vardır:

- Hata *ayıklayıcı tarafı,* hata ayıklayıcısının Visual Studio çalışır. Hata ayıklayıcı tarafı kodu görselleştiriciniz için kullanıcı arabirimini oluşturur ve görüntüler.

- Hata *ayıklayıcısı tarafı,* hata ayıklarken Visual Studio işlem içinde çalışır *(hata ayıklayıcısı).*

  Görselleştirici, hata ayıklayıcının bir veri nesnesininiçeriğini anlamlı ve anlaşılır bir şekilde görüntülemesi (görselleştirmesi) sağlayan bir hata ayıklayıcı bileşenidir. Bazı görselleştiriciler veri nesnesinin düzenlenmesini de destekler. Özel görselleştiriciler yazarak, hata ayıklayıcısını kendi özel veri türlerinizi işlemek üzere genişletebilirsiniz.

  Görselleştirilen veri nesnesi, hata ayıklama işlemi (hata ayıklama *işlemi) içinde* yer alır. Verileri görüntüecek kullanıcı arabirimi, hata ayıklayıcısı Visual Studio oluşturulur:

|Hata Ayıklayıcı İşlem|Hata Ayıklama süreci|
|----------------------|----------------------|
|Hata ayıklayıcısı kullanıcı arabirimi (DataTips, Watch Window, QuickWatch)|Görselleştirilen Veri Nesnesi|

 Hata ayıklayıcı arabiriminde veri nesnesini görselleştirmek için iki işlem arasında iletişim kurmak için koda ihtiyacınız vardır. Sonuç olarak, görselleştirici mimarisi iki bölümden oluşur: hata *ayıklayıcı tarafı* kodu *ve hata ayıklama tarafı* kodu.

 Hata ayıklayıcı tarafı kodu kendi kullanıcı arabirimini oluşturur. Bu arabirim DataTip, Watch Window veya QuickWatch gibi hata ayıklayıcı arabiriminden çağrılabilir. Görselleştirici arabirimi, sınıfı ve arabirimi <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> kullanılarak <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> oluşturulur. Tüm Görselleştirici API'leri gibi DialogDebuggerVisualizer ve IDialogVisualizerService ad alanı içinde <xref:Microsoft.VisualStudio.DebuggerVisualizers> bulunur.

|Hata Ayıklayıcı Tarafı|Hata Ayıklayıcısı Tarafı|
|-------------------|-------------------|
|DialogDebuggerVisualizer Sınıfı<br /><br /> IDialogVisualizerService Arabirimi|Veri Nesnesi|

 Kullanıcı arabirimi, hata ayıklayıcı tarafında bulunan bir Nesne Sağlayıcısından görselleştirilen verileri alır:

|Hata Ayıklayıcı Tarafı|Hata Ayıklayıcısı Tarafı|
|-------------------|-------------------|
|DialogDebuggerVisualizer Sınıfı<br /><br /> IDialogVisualizerService Arabirimi|Veri Nesnesi|
|Nesne Sağlayıcısı <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> (uygulayan)||

 Hata ayıklayıcı tarafında Nesne Kaynağı adlı karşılık gelen bir nesne vardır:

|Hata Ayıklayıcı Tarafı|Hata Ayıklayıcısı Tarafı|
|-------------------|-------------------|
|DialogDebuggerVisualizer Sınıfı<br /><br /> IDialogVisualizerService Arabirimi|Veri Nesnesi|
|Nesne Sağlayıcısı <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> (uygulayan)|Nesne Kaynağı (türetilen <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> )|

 Nesne Sağlayıcısı görselleştirici kullanıcı arabirimine görselleştirilen nesne verilerini sağlar. Nesne Sağlayıcısı nesne verilerini Nesne Kaynağından alır. Nesne Sağlayıcısı ve Nesne Kaynağı, hata ayıklayıcı tarafı ile debugee tarafı arasında nesne verilerini iletişim kurmak için API'ler sağlar.

 Her görselleştiricinin görselleştirilen veri nesnesini aldırmaları gerekir. Aşağıdaki tabloda, Nesne Sağlayıcısı ve Nesne Kaynağı'nın bu amaçla kullanmakta olduğu ilgili API'ler yer alır:

|Nesne Sağlayıcısı|Nesne Kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Nesne sağlayıcısının veya kullanabileceğine dikkat <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> olun. Her iki API de Nesne Kaynağında <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> çağrısıyla sonuç verir. görselleştirilen nesnenin serileştirilmiş bir formunu temsil eden bir doldurma <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> <xref:System.IO.Stream?displayProperty=fullName> çağrısı.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> verileri yeniden nesne formuna geri deserialize eder, bu formda daha sonra ile oluştursanız kullanıcı arabiriminde <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> görüntüebilirsiniz. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> , verileri ham olarak doldurur ve `Stream` bu da kendinizin deserialize olması gerekir. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> , serileştirilmiş <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> almak için çağrısıyla `Stream` çalışır, ardından verileri seri halden çıkartır. Nesne <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> .NET tarafından seri hale getirilemez ve özel serileştirme gerektirdiği zaman kullanın. Bu durumda, yöntemini de geçersiz <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> kılmalı.

 Salt okunur bir görselleştirici oluşturuyorsanız veya ile tek yol iletişim <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> yeterlidir. Veri nesnelerini düzenlemeyi destekleyen bir görselleştirici oluşturuyorsanız, daha fazlasını yapmak gerekir. Nesne Sağlayıcısından nesne kaynağına da bir veri nesnesi gönderebilirsiniz. Aşağıdaki tabloda bu amaç için kullanılan Nesne Sağlayıcısı ve Nesne Kaynağı API'leri yer alır:

|Nesne Sağlayıcısı|Nesne Kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Nesne Sağlayıcısı'nın kullanabileceği iki API olduğunu da yine fark edersiniz. Veriler her zaman Nesne Sağlayıcısından Nesne Kaynağına olarak gönderilir, ancak `Stream` nesneyi kendiniz seri hale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> getirmeniz `Stream` gerekir.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> , sizin sağ istediğiniz bir nesneyi alır, bir içinde seri hale `Stream` getirmez, ardından <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> çağrısıyla 'a `Stream` <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> gönderir.

 Replace yöntemlerinden birini kullanarak, hata ayıklayıcıda görselleştiriken nesnesinin yerini alan yeni bir veri nesnesi oluşturur. Özgün nesnenin içeriğini değiştirmeden değiştirmek için aşağıdaki tabloda gösterilen Transfer yöntemlerinden birini kullanın. Bu API'ler görselleştirildi olan nesneyi değiştirmeden verileri aynı anda her iki yönde de aktarıyor:

|Nesne Sağlayıcısı|Nesne Kaynağı|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —veya—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [İzlenecek Yol: Visual Basic'de Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Görselleştirici Güvenlik Konuları](../debugger/visualizer-security-considerations.md)