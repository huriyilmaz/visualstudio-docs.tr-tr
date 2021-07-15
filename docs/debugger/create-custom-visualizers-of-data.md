---
title: Özel veri görselleştiricileri oluşturma | Microsoft Docs
description: Visual Studio ayıklayıcı görselleştiricileri, verileri görüntü alan bileşenlerdir. Altı standart görselleştirici hakkında bilgi ve başkalarını nasıl yazabilir veya indiry bazılarınız hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
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
ms.openlocfilehash: b8310133520231434ba7ed342a5e855892e3c53a
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201747"
---
# <a name="create-custom-data-visualizers"></a>Özel veri görselleştiricileri oluşturma

 *Görselleştirici,* bir değişkeni veya nesneyi veri türüne uygun şekilde görüntüleyen hata [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ayıklayıcısı kullanıcı arabiriminin bir parçasıdır. Örneğin, BIR HTML görselleştiricisi bir HTML dizesini yorumlar ve sonucu tarayıcı penceresinde görünecek şekilde görüntüler. Bit eşlem görselleştiricisi bir bit eşlem yapısını yorumlar ve temsil ettiği grafiği görüntüler. Bazı görselleştiriciler verileri hem değiştirmenizi hem de görüntülemenizi sağlar.

 Hata [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ayıklayıcısı altı standart görselleştirici içerir. Metin, HTML, XML ve JSON görselleştiricileri dize nesneleri üzerinde çalışır. WPF Ağacı görselleştiricisi, bir WPF nesne görsel ağacının özelliklerini görüntüler. Veri kümesi görselleştiricisi DataSet, DataView ve DataTable nesneleri için çalışır.

Daha fazla görselleştirici Microsoft, üçüncü taraflar ve topluluktan indirilebilir. Ayrıca kendi görselleştiricilerinizi yazabilir ve hata [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ayıklayıcısına yükleyebilirsiniz.

Hata ayıklayıcısında görselleştirici bir büyüteç simgesi ![VisualizerIcon ile temsil edildi.](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") Bir **DataTip**, hata ayıklayıcı  İzleme penceresi veya **QuickWatch** iletişim kutusunda simgeyi ve ardından ilgili nesne için uygun görselleştiriciyi seçin.

## <a name="write-custom-visualizers"></a>Özel görselleştiriciler yazma

 > [!NOTE]
 > Yerel kod için özel görselleştirici oluşturmak üzere [SQLite yerel Hata Ayıklayıcı Görselleştiricisi örneğine](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) bakın. Özel görselleştiriciler UWP ve Windows 8.x uygulamaları için desteklenmiyor.

ve dışında herhangi bir yönetilen sınıfın nesnesi için özel bir görselleştirici <xref:System.Object> <xref:System.Array> yazabilirsiniz.

Hata ayıklayıcı görselleştiricisi mimarisinin iki bölümü vardır:

- Hata *ayıklayıcı tarafı,* hata Visual Studio içinde çalışır ve görselleştirici kullanıcı arabirimini oluşturur ve görüntüler.

- Hata *ayıklayıcı tarafı,* hata ayıklarken Visual Studio işlem içinde çalışır *(hata ayıklayıcısı).* Görselleştirmek için veri nesnesi (örneğin, bir Dize nesnesi) hata ayıklama işlemi içinde mevcuttur. Hata ayıklayıcısı tarafı, nesneyi hata ayıklayıcı tarafına gönderir ve bu da nesneyi, kendi oluştur aldığınız kullanıcı arabiriminde görüntüler.

Hata ayıklayıcı tarafı, arabirimi uygulayan *bir nesne sağlayıcısından* veri nesnesini <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> alır. Hata ayıklayıcısı tarafı, nesnesinden *türetilen* nesne kaynağı aracılığıyla <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> gönderir.

Nesne sağlayıcısı ayrıca verileri yeniden nesne kaynağına gönderebilir ve bu sayede verileri düzenleyemezsiniz. İfade değerlendiricisi ve nesne kaynağıyla konuşmak için nesne sağlayıcısını geçersiz kılar.

Hata ayıklayıcı tarafı ve hata ayıklayıcı tarafı, bir veri nesnesini bir içinde seri hale getirme ve bir veri nesnesine geri seri halinde seri hale getirme yöntemleri <xref:System.IO.Stream> <xref:System.IO.Stream> aracılığıyla birbirleriyle iletişim <xref:System.IO.Stream> kurar.

Görselleştiriciyi yalnızca tür açık bir türse genel tür için yazabilir. Bu kısıtlama, özniteliğini kullanırken kısıtlamayla `DebuggerTypeProxy` aynıdır. Ayrıntılar için [bkz. DebuggerTypeProxy özniteliğini kullanma.](../debugger/using-debuggertypeproxy-attribute.md)

Özel görselleştiricilerde güvenlikle ilgili dikkat edilmesi gereken noktalar olabilir. Bkz. [Görselleştirici güvenliğiyle ilgili dikkat edilmesi gerekenler.](../debugger/visualizer-security-considerations.md)

Aşağıdaki adımlar görselleştirici oluşturma hakkında üst düzey bir genel bakış sağlar. Ayrıntılı yönergeler için [bkz. Kılavuz: C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) ile görselleştirici yazma veya [Kılavuz: Görselleştiriciyi Visual Basic.](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)

### <a name="to-create-the-debugger-side"></a>Hata ayıklayıcı tarafı oluşturmak için

Hata ayıklayıcı tarafında görselleştirici kullanıcı arabirimini oluşturmak için, 'den devralan bir sınıf oluşturun ve arabirimini <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> görüntülemek için yöntemini geçersiz <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> kılın. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>Görselleştiricide form, Windows ve denetimleri görüntülemek için kullanabilirsiniz.

1. Hata <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> ayıklayıcı tarafında görselleştirilmiş nesneyi almak için yöntemleri kullanın.

1. 'den devralan bir sınıf <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> oluşturun.

1. Arabiriminizi <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> görüntülemek için yöntemini geçersiz kılın. Arabirimde <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> form, Windows ve denetimleri görüntülemek için yöntemleri kullanın.

1. Uygula, <xref:System.Diagnostics.DebuggerVisualizerAttribute> görüntü için görselleştiriciyi () <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> vererek.

#### <a name="special-debugger-side-considerations-for-net-50"></a>.NET 5.0+ için özel hata ayıklayıcı tarafı konuları

Özel Görselleştiriciler, varsayılan olarak  *sınıfını kullanarak* ikili serileştirme aracılığıyla hata ayıklayıcı ve hata ayıklayıcı <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> tarafları arasında veri aktarımı sağlar. Ancak, bu tür serileştirmeler .NET 5 ve üzerinde düzeltilemez güvenlik açıkları ile ilgili güvenlik kaygıları *nedeniyle giderildi.*
Ayrıca, 5. ASP.NET Core tamamen kullanımdan kaldırılmış olarak işaretlenir ve kullanımı ASP.NET Core [belgelerinde açıklandığı gibi atacaktır.](/dotnet/core/compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete)
Bu nedenle, bu bölümde görselleştiricinizin bu senaryoda hala desteklensin diye atılması gereken gerekli adımlar açıklandı.

- Uyumluluk nedenleriyle, <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A> önceki bölümde geçersiz kılınan yöntemi yine de bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> alır. Yine de, aslında <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider2> türündedir.
Bu nedenle, `objectProvider` nesneyi güncelleştirilmiş arabirime atabilirsiniz.

- Komutlar veya veriler gibi nesneleri  hata ayıklayıcı tarafına gönderirken, bir akışa göndermek için yöntemini kullanır, hata ayıklama işleminin çalışma zamanlarına göre kullanmak üzere en iyi serileştirme biçimini `IVisualizerObjectProvider2.Serialize` belirler. 
Ardından, akışı yöntemine `IVisualizerObjectProvider2.TransferData` iletir.

- Hata *ayıklayıcı tarafı görselleştirici* bileşeninin hata ayıklayıcı tarafına herhangi bir şey geri dönmesi *gerekirse,* yöntemi tarafından <xref:System.IO.Stream> döndürülen nesnesinde <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A> bulunur. Bir örneği `IVisualizerObjectProvider2.GetDeserializableObjectFrom` almak ve gerektiğinde işleme almak için yöntemini <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> kullanın.

İkili Serileştirme desteklenmemektedir. Hata ayıklama tarafında hangi diğer değişikliklerin gerekli olduğunu öğrenmek için  [.NET 5.0+](#special-debuggee-side-considerations-for-net-50) için özel hata ayıklama tarafı konuları bölümüne bakın.

> [!NOTE]
> Sorun hakkında daha fazla bilgi almak için [binaryFormatter güvenlik kılavuzuna bakın.](/dotnet/standard/serialization/binaryformatter-security-guide)

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Hata ayıklayıcı tarafı için görselleştirici nesnesi kaynağı oluşturmak için

Hata ayıklayıcı yan kodunda, görselleştirilen türü (hata ayıklayıcı tarafı nesne <xref:System.Diagnostics.DebuggerVisualizerAttribute> kaynağı) () vererek <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> düzenleyin. özelliği `Target` nesne kaynağını ayarlar. Nesne kaynağını atlarsanız görselleştirici varsayılan bir nesne kaynağı kullanır.

::: moniker range=">=vs-2019"
Hata ayıklayıcısı yan kodu, görselleştirilmiş nesne kaynağını içerir. Veri nesnesi, yöntemlerini geçersiz <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> kabilirsiniz. Tek başına görselleştirici oluşturmak için hata ayıklama tarafı DLL gereklidir.
::: moniker-end

Hata ayıklama tarafı kodunda:

- Görselleştiricinin veri nesnelerini düzenlemesine izin ver için nesne kaynağının veya yöntemlerinden devralması ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> geçersiz `TransferData` k olması `CreateReplacementObject` gerekir.

- Görselleştiricide çoklu hedeflemeyi desteklemeniz gerekirse hata ayıklama tarafı proje dosyasında aşağıdaki Hedef Çerçeve Bilinen Adlarını (TFM) kullanabilirsiniz.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Desteklenen tek TFM'ler bunlardır.

#### <a name="special-debuggee-side-considerations-for-net-50"></a>.NET 5.0+ için özel hata ayıklama tarafı konuları

> [!IMPORTANT]
> Varsayılan olarak kullanılan temel ikili serileştirme yöntemiyle ilgili güvenlik kaygıları nedeniyle görselleştiricinin .NET 5.0 ve üzerinde çalışması için ek adımlar gerekli olabilir. Devam etmeden önce [lütfen bu](#special-debugger-side-considerations-for-net-50) bölümü okuyun.

- Görselleştirici yöntemini <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A> uygulayıyorsa, en son sürümünde <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetDeserializableObject%2A> kullanılabilen yeni eklenen yöntemini `VisualizerObjectSource` kullanın. Döndüren, nesnenin serileştirme biçimini (ikili veya JSON) belirlemeye ve temel alınan nesneyi seri halinden çıkarmak ve <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDeserializableObject> kullanılmaktadır.

- Hata *ayıklayıcısı tarafı,* çağrının  bir parçası olarak hata ayıklayıcı tarafına veri döndürürse, yöntemi aracılığıyla hata ayıklayıcısının akışına yanıtı `TransferData` seri hale  <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A> getirme.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: C# dilinde görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [İzlenecek yol: Visual Basic'te görselleştirici yazma](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Nasıl yapılır: Görselleştirici yükleme](../debugger/how-to-install-a-visualizer.md)
- [Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Görselleştirici API başvurusu](../debugger/visualizer-api-reference.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
