---
title: Özel veri Görselleştiriciler oluştur | Microsoft Docs
description: Visual Studio hata ayıklayıcı görselleştiriciler, verileri görüntüleyen bileşenlerdir. Altı standart Görselleştiriciler ve diğer kişilerin nasıl yazılacağı veya indirileceği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/29/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5f2beccbc4004b9b36b7ff1c39b3ad60cc39120
ms.sourcegitcommit: 24dd8fbdf88eca005e9f01328ab57150de37d432
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2021
ms.locfileid: "115014834"
---
# <a name="create-custom-data-visualizers"></a>Özel veri Görselleştiriciler oluşturma

 *Görselleştirici* , bir [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] değişken veya nesneyi veri türüne uygun bir şekilde görüntüleyen hata ayıklayıcı Kullanıcı arabiriminin bir parçasıdır. Örneğin, bir HTML Görselleştiricisini bir HTML dizesini yorumlar ve bir tarayıcı penceresinde görüneceği şekilde sonucu görüntüler. Bit eşlem görselleştiricisi bir bit eşlem yapısını Yorumlar ve temsil ettiği grafiği görüntüler. Bazı Görselleştiriciler, değişiklik yapmanızı ve verileri görüntülemenizi sağlar.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Hata ayıklayıcı altı standart Görselleştiriciler içerir. Metin, HTML, XML ve JSON Görselleştiriciler dize nesnelerinde çalışır. WPF ağaç görselleştiricisi, WPF nesne görsel ağacının özelliklerini görüntüler. Veri kümesi görselleştiricisi veri kümesi, DataView ve DataTable nesneleri için geçerlidir.

Daha fazla Görselleştiriciler Microsoft, üçüncü taraflar ve topluluk tarafından indirilebilir. Ayrıca kendi görselleştiricilerini yazıp [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] hata ayıklayıcıya yükleyebilirsiniz.

Hata ayıklayıcıda bir Görselleştirici bir büyüteç simgesi ![Visualizersimgesiyle](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")temsil edilir. Bir **Datatıp**, Debugger **Gözcü** penceresinde veya **QuickWatch** iletişim kutusunda simgeyi seçebilir ve ardından karşılık gelen nesne için uygun görselleştiricisi seçebilirsiniz.

## <a name="write-custom-visualizers"></a>Özel Görselleştiriciler yazma

 > [!NOTE]
 > Yerel kod için özel bir Görselleştirici oluşturmak için, bkz. [SQLite yerel hata ayıklayıcı görselleştiricisi](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) örneği. UWP ve Windows 8. x uygulamaları için özel görselleştiriciler desteklenmez.

Ve hariç olmak üzere, herhangi bir yönetilen sınıfın nesnesi için özel bir Görselleştirici <xref:System.Object> yazabilirsiniz <xref:System.Array> .

Bir hata ayıklayıcı görselleştiricisi mimarisi iki bölümden oluşur:

- *hata ayıklayıcı tarafı* Visual Studio hata ayıklayıcı içinde çalışır ve görselleştirici kullanıcı arabirimini oluşturur ve görüntüler. 

  Visual Studio, .NET Framework çalışma zamanında yürütüldüğü için, bu bileşenin .NET Framework için yazılması gerekir. Bu nedenle, .NET Core için yazmak mümkün değildir.

- hata *ayıklanan yan* Visual Studio işlem içinde çalışıyor (hata *ayıklanan*). Hata ayıklanan işlemde görselleştirilecek veri nesnesi (örneğin, bir dize nesnesi) var. Hata ayıklanan yüz, nesneyi oluşturduğunuz Kullanıcı arabiriminde görüntüleyen hata ayıklayıcı tarafına gönderir.

  bu bileşeni oluşturduğunuz çalışma zamanının, hata ayıklanan işlemin çalışacağı, diğer bir deyişle .NET Framework veya .net Core ile eşleşmesi gerekir.

Hata ayıklayıcı tarafı, arabirimini uygulayan bir *nesne sağlayıcısından* veri nesnesini alır <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . Hata ayıklanan yüz, nesnesini öğesinden türetilen *nesne kaynağı* üzerinden gönderir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Nesne sağlayıcısı Ayrıca verileri nesne kaynağına geri gönderebilir ve bu sayede verileri düzenleyebilen bir Görselleştirici yazmanızı sağlayabilirsiniz. İfade değerlendiricisi ve nesne kaynağıyla konuşmak için nesne sağlayıcısını geçersiz kılabilirsiniz.

Hata ayıklanan yan ve hata ayıklayıcı tarafı, <xref:System.IO.Stream> bir veri nesnesini bir ' a seri hale getirmek <xref:System.IO.Stream> ve bir veri nesnesine geri serisini kaldırmak için yöntemler aracılığıyla birbirleriyle iletişim kurar <xref:System.IO.Stream> .

Yalnızca tür açık bir tür ise, genel bir tür için Görselleştirici yazabilirsiniz. Bu kısıtlama, özniteliği kullanılırken kısıtlama ile aynıdır `DebuggerTypeProxy` . Ayrıntılar için bkz. [DebuggerTypeProxy özniteliğini kullanma](../debugger/using-debuggertypeproxy-attribute.md).

Özel görselleştiricilerin güvenlik konuları olabilir. Bkz. [Görselleştirici güvenlik konuları](../debugger/visualizer-security-considerations.md).

Aşağıdaki adımlarda, görselleştiricisi oluşturmaya yönelik üst düzey bir genel bakış sunulmaktadır. Ayrıntılı yönergeler için bkz. [Izlenecek yol: C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) veya [izlenecek yol: Visual Basic bir Görselleştirici](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)yazma.

### <a name="to-create-the-debugger-side"></a>Hata ayıklayıcı tarafını oluşturmak için

Hata ayıklayıcı tarafında görselleştiricisi Kullanıcı arabirimini oluşturmak için, öğesinden devralan bir sınıf oluşturur <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> arabirimi göstermek için yöntemi geçersiz kılar. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>görselleştiricinizdeki Windows formları, iletişimleri ve denetimleri göstermek için kullanabilirsiniz.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>Hata ayıklayıcı tarafında görselleştirilen nesneyi almak için yöntemleri kullanın.

1. Öğesinden devralan bir sınıf oluşturun <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>Arabiriminizi göstermek için yöntemini geçersiz kılın. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>arabiriminizdeki Windows formları, iletişimleri ve denetimleri göstermek için yöntemler kullanın.

1. <xref:System.Diagnostics.DebuggerVisualizerAttribute>Görselin () görüntülemesini sağlayan bir uygulama <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .

#### <a name="special-debugger-side-considerations-for-net-50"></a>.NET 5.0 + için özel hata ayıklayıcı tarafı konuları

Özel Görselleştiriciler, varsayılan olarak sınıfını kullanarak hata *ayıklanan* ve *hata ayıklayıcı* tarafları arasında verileri ikili serileştirme aracılığıyla aktarır <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . Bununla birlikte, bu tür bir serileştirme .NET 5 ve üzeri bir *güvenlik açığına yönelik güvenlik sorunları* nedeniyle bu tür bir serileştirme.
üstelik, ASP.NET Core 5 ' te tamamen kullanımdan kaldırılmıştır ve kullanımı [ASP.NET Core belgelerinde](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete)açıklandığı gibi oluşturulur.
Bu bölümde, Görselleştiricinizi Bu senaryoda hala desteklendiğinden emin olmak için gerçekleştirmeniz gereken adımlar açıklanmaktadır.

- Uyumluluk nedenleriyle, <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> önceki bölümde geçersiz kılınan yöntem de ' de sürer <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . ancak, Visual Studio 2019 sürüm 16,10 ' den itibaren, aslında tür <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2> .
Bu nedenle, `objectProvider` nesneyi güncelleştirilmiş arabirime atayın.

- Komut veya veriler gibi nesneleri gönderirken *hata ayıklanan tarafa* `IVisualizerObjectProvider2.Serialize` bir akışa geçirmek için yöntemini kullanırken, *hata ayıklanan* işlemin çalışma zamanına göre kullanılacak en iyi serileştirme biçimini tespit eder.
Ardından, akışı `IVisualizerObjectProvider2.TransferData` yöntemine geçirin.

- *Debugayıklanan taraf* görselleştiricisi bileşeninin *hata ayıklayıcı tarafına* herhangi bir şey döndürmesi gerekiyorsa, <xref:System.IO.Stream> yöntemi tarafından döndürülen nesnede bulunur <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A> . Yöntemini kullanarak `IVisualizerObjectProvider2.GetDeserializableObjectFrom` bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> örneği alın ve gereken şekilde işleyin.

Ikili serileştirme kullanılırken *hata ayıklanan tarafında* başka değişiklikler yapılması gerektiğini öğrenmek için lütfen [.NET 5.0 + bölümüne yönelik özel hata ayıklama tarafı konuları](#special-debuggee-side-considerations-for-net-50) ' na bakın.

> [!NOTE]
> Sorun hakkında daha fazla bilgi isterseniz, [BinaryFormatter Güvenlik Kılavuzu](/dotnet/standard/serialization/binaryformatter-security-guide)' na bakın.

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Hata ayıklanan kenar için Görselleştirici nesne kaynağını oluşturmak için

Hata ayıklayıcı tarafı kodunda, <xref:System.Diagnostics.DebuggerVisualizerAttribute> öğesini, görselleştirilecek türü (hata ayıklanan-yan nesne kaynağı) () vererek düzenleyin <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . `Target`Özelliği, nesne kaynağını ayarlar. Nesne kaynağını atlarsanız, Görselleştirici varsayılan bir nesne kaynağı kullanacaktır.

::: moniker range=">=vs-2019"
Hata ayıklanan yüz kodu görselleştirilen nesne kaynağını içerir. Veri nesnesi yöntemlerini geçersiz kılabilir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Bağımsız bir Görselleştirici oluşturmak istiyorsanız, bir debugayıklanan yan DLL gereklidir.
::: moniker-end

Hata ayıklanan taraf kodunda:

- Görselleştirici veri nesnelerini düzenlemesine izin vermek için, nesne kaynağı from kaynağından devralması <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ve ya da yöntemlerini geçersiz kılmalıdır `TransferData` `CreateReplacementObject` .

- Görselleştiricinizdeki çoklu hedef belirleme 'yı desteklemeniz gerekiyorsa, hata ayıklanan-tarafı proje dosyasında aşağıdaki hedef Framework takma adlarını (TFMs) kullanabilirsiniz.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Bunlar desteklenen tek TFMs ' dir.

#### <a name="special-debuggee-side-considerations-for-net-50"></a>.NET 5.0 + için özel hata ayıklama tarafı konuları

> [!IMPORTANT]
> Varsayılan olarak kullanılan temel ikili serileştirme yöntemiyle ilgili güvenlik sorunları nedeniyle Görselleştirici .NET 5,0 ' de çalışmaya başlaması için ek adımlar gerekebilir. Lütfen devam etmeden önce bu [bölümü](#special-debugger-side-considerations-for-net-50) okuyun.

- Görselleştiricisi yöntemini uygularsa <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> , <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> en son sürümünde bulunan yeni eklenen yöntemi kullanın `VisualizerObjectSource` . <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject>Bu, nesnenin serileştirme biçimini (ikili veya JSON) belirlemesine ve temel alınan nesnenin kullanılabilir olması için serisini kaldırmanıza yardımcı olur.

- Hata *ayıklanan taraf* , çağrının bir parçası olarak *hata ayıklayıcı tarafına* veri döndürürse `TransferData` , yöntemi aracılığıyla *hata ayıklayıcı tarafındaki* akışa yanıtı serileştirme <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: C# dilinde görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [İzlenecek yol: Visual Basic'te görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Nasıl yapılır: Görselleştirici yükleme](../debugger/how-to-install-a-visualizer.md)
- [Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Görselleştirici API başvurusu](../debugger/visualizer-api-reference.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
