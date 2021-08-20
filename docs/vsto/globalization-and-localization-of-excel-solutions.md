---
title: Excel çözümlerin genelleştirme ve yerelleştirilmesi
description: Windows için ingilizce olmayan ayarlara sahip bilgisayarlarda çalıştırılacak Microsoft Office Excel çözümleri için özel konular hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 331b68bdcf2ed65de6f60b5abb79d45e2b4a07ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139900"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Excel çözümlerin genelleştirme ve yerelleştirilmesi
  bu bölüm, Windows için ingilizce olmayan ayarlara sahip bilgisayarlarda çalıştırılacak Microsoft Office Excel çözümleri için özel hususlar hakkında bilgiler içerir. Microsoft Office çözümlerin çoğu yönü, Visual Studio kullanarak diğer tür çözümler oluştururken karşılaştığınız ile aynıdır. Genel bilgiler için bkz. [globalize ve yerelleştirme uygulamaları](../ide/globalizing-and-localizing-applications.md).

 varsayılan olarak Microsoft Office Excel ana bilgisayar denetimleri, yönetilen kod kullanılarak geçirilen veya geçen tüm veriler ingilizce (Birleşik Devletler) biçimlendirme kullanılarak biçimlendirilmediği sürece, herhangi bir Windows bölgesel ayarında doğru şekilde çalışır. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya öğesini hedefleyen projelerde [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , bu davranış ortak dil çalışma zamanı (CLR) tarafından denetlenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Excel verileri çeşitli bölgesel ayarlarla biçimlendirin
 tarih ve para birimi gibi yerel ayara duyarlı biçimlendirmeye sahip tüm verileri, Microsoft Office Excel geçirmeden veya Office projenizdeki koddan okurken önce, ingilizce (Birleşik Devletler) veri biçimini (locale ıd 1033) kullanarak biçimlendirmeniz gerekir.

 varsayılan olarak, Visual Studio bir Office çözümü geliştirirken Excel nesne modeli, yerel ayar kimliği 1033 veri biçimlendirmesini bekler (buna ayrıca nesne modelinin yerel ayar kimliği 1033 ' ye kilitlenmesi de denir). bu davranış, Visual Basic for Applications çalışma yöntemiyle eşleşir. ancak, Office çözümlerinizde bu davranışı değiştirebilirsiniz.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Excel nesne modelinin her zaman yerel ayar kimliğini nasıl beklediğini anlayın 1033
 varsayılan olarak, Visual Studio kullanarak oluşturduğunuz Office çözümleri, son kullanıcının yerel ayarlarından etkilenmez ve her zaman yerel ayar ingilizce (Birleşik Devletler) gibi davranır. örneğin, Excel özelliği alırsanız veya ayarlarsanız <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> , verilerin yerel ayar kimliği 1033 ' nin beklediği şekilde biçimlendirilmesi gerekir. Farklı bir veri biçimi kullanırsanız, beklenmeyen sonuçlar alabilirsiniz.

 yönetilen kod tarafından iletilen veya geçirilen veriler için ingilizce (Birleşik Devletler) biçimini kullansanız bile, Excel verileri son kullanıcının yerel ayarlarına göre doğru şekilde yorumlar ve görüntüler. Excel yönetilen 1033 kod, verilerin ingilizce (Birleşik Devletler) biçiminde olduğunu ve bu nedenle kullanıcının yerel ayarıyla eşleşecek şekilde yeniden biçimlendirilmesi gerektiğini belirten verilerle birlikte, verileri doğru şekilde biçimlendirebilir.

 Örneğin, son kullanıcılar bölgesel seçeneklerinin Almanca (Almanya) yerel ayarı olarak ayarlanmış olması halinde, 29 Haziran 2005 tarihleri şu şekilde biçimlendirilecek şekilde bekler: 29.06.2005. ancak çözümünüzün tarihi bir dize olarak Excel geçirirse, tarihi ingilizce (Birleşik Devletler) biçimine göre biçimlendirmeniz gerekir: 6/29/2005. hücre bir tarih hücresi olarak biçimlenir Excel, tarihi almanca (almanya) biçiminde görüntüler.

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>diğer yerel kimlik kimliklerini Excel nesne modeline geçirin
 ortak dil çalışma zamanı (CLR), yerel ayara duyarlı verileri kabul eden Excel nesne modelindeki tüm yöntemlere ve özelliklere otomatik olarak 1033 ön eki geçirir. Nesne modeline yapılan tüm çağrılar için bu davranışı otomatik olarak değiştirme yolu yoktur. Ancak, <xref:System.Type.InvokeMember%2A> yöntemini çağırmak ve yerel ayar kimliğini metodun *kültür* parametresine geçirerek, kullanarak belirli bir yönteme farklı BIR yerel ayar kimliği geçirebilirsiniz.

## <a name="localize-document-text"></a>Belge metnini yerelleştirin
 Projenizdeki belge, şablon veya çalışma kitabı muhtemelen, derlemeden ve diğer yönetilen kaynaklardan ayrı olarak yerelleştirilmesi gereken statik metni içerir. bunu yapmanın kolay bir yolu, belgenin bir kopyasını oluşturmak ve metni Microsoft Office Word veya Microsoft Office Excel kullanarak çevirmedir. Herhangi bir sayıda belge aynı derlemeye bağlanabileceğinden, bu işlem kodda değişiklik yapmasanız bile işe yarar.

 yine de, belge metniyle etkileşim kuran kodunuzun herhangi bir bölümünün metnin diliyle eşleşecek şekilde devam ettiğinden ve bu yer işaretleri, adlandırılmış aralıklar ve diğer görüntüleme alanları, farklı dilbilgisi ve metin uzunluğunun ayarlanması için gereken Office belgenin herhangi bir yeniden biçimlendirme işlemiyle aynı olduğundan emin olmanız gerekir. Görece küçük metin içeren belge şablonlarında, metni kaynak dosyalarında depolamayı ve sonra metni çalışma zamanında yüklemeyi düşünmek isteyebilirsiniz.

### <a name="text-direction"></a>Metin yönü
 Excel, çalışma sayfasının bir özelliğini metni sağdan sola işleyecek şekilde ayarlayabilirsiniz. Tasarımcı üzerine yerleştirilmiş konak denetimleri veya bir özelliği olan denetim, `RightToLeft` çalışma zamanında otomatik olarak bu ayarlarla eşleşir. Word, çift yönlü metin için bir belge ayarına sahip değildir (yalnızca metin hizalamasını değiştirirsiniz), bu nedenle denetimler bu ayarla eşlenemez. Bunun yerine, her denetim için metin hizalamasını ayarlamanız gerekir. Tüm denetimlerin üzerinde gezinmek için kod yazmak ve bunları sağdan sola metin işlemeye zorlamak mümkündür.

### <a name="change-culture"></a>Kültürü Değiştir
 belge düzeyi özelleştirme kodunuz genellikle Excel ana uı iş parçacığını paylaşır, bu nedenle iş parçacığı kültürü üzerinde yaptığınız tüm değişiklikler o iş parçacığında çalışan diğer her şeyi etkiler; değişiklik, özelleştirmeinizdeki kısıtlı değildir.

 Windows Forms denetimleri, uygulama düzeyi VSTO eklentileri ana bilgisayar uygulaması tarafından başlatılmadan önce başlatılır. Bu durumlarda, Kullanıcı arabirimi denetimleri ayarlamadan önce kültür değiştirilmelidir.

## <a name="install-the-language-packs"></a>Dil paketlerini yükler
 Windows için ingilizce olmayan ayarlara sahipseniz, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows aynı dildeki iletileri görmek için dil paketlerini yükleyebilirsiniz. herhangi bir son kullanıcı çözümlerinizi Windows için ingilizce olmayan ayarlarla çalıştırırsanız, çalışma zamanı iletilerini Windows aynı dilde görmek için doğru dil paketine sahip olmaları gerekir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Dil paketleri [Microsoft İndirme Merkezi](https://www.microsoft.com/download)' nden edinilebilir.

 ayrıca, ClickOnce iletileri için yeniden dağıtılabilir .NET Framework dil paketleri gereklidir. .NET Framework dil paketleri [Microsoft indirme merkezi](https://www.microsoft.com/download)' nden edinilebilir.

## <a name="regional-settings-and-excel-com-calls"></a>bölgesel ayarlar ve Excel COM çağrıları
 Yönetilen bir istemci bir COM nesnesinde bir yöntemi çağırdığında ve kültüre özgü bilgileri geçmesi gerektiğinde, bu, <xref:System.Globalization.CultureInfo.CurrentCulture%2A> geçerli iş parçacığı yerel ayarıyla eşleşen (yerel ayar) öğesini de kullanıyor. Geçerli iş parçacığı yerel ayarı, kullanıcının bölgesel ayarlarından varsayılan olarak devralınır. ancak, Visual Studio içindeki Office geliştirme araçları kullanılarak oluşturulan bir Excel çözümünden Excel nesne modeline bir çağrı yaptığınızda, ingilizce (Birleşik Devletler) veri biçimi (yerel ayar kimliği 1033), Excel nesne modeline otomatik olarak geçirilir. tarih ve para birimi gibi yerel ayara duyarlı biçimlendirmeye sahip tüm verileri, Microsoft Office Excel geçirmeden veya proje kodunuzda verileri okuyabilmeniz için önce ingilizce (Birleşik Devletler) veri biçimini kullanarak biçimlendirmeniz gerekir.

## <a name="considerations-for-storing-data"></a>Veri depolamaya ilişkin önemli noktalar
 verilerinizin doğru şekilde yorumlanıp görüntülendiğinden emin olmak için, bir uygulama verileri, Excel çalışma sayfası formülleri gibi, kesin türü belirtilmiş nesneler yerine dize sabit değerleri (sabit kodlanmış) olarak depoladığında oluşabilecek sorunları da göz önünde bulundurmanız gerekir. Kültür sabiti veya Ingilizce (Birleşik Devletler) (LCıD değeri 1033) stili olarak biçimlendirilen verileri kullanmanız gerekir.

### <a name="applications-that-use-string-literals"></a>Dize sabit değerleri kullanan uygulamalar
 sabit olarak kodlanmış olabilecek olası değerler arasında, ingilizce (Birleşik Devletler) biçiminde yazılmış tarih değişmez değerleri ve yerelleştirilmiş işlev adlarını içeren çalışma sayfası formülleri Excel. Başka bir olasılık da "1.000" gibi bir sayı içeren sabit kodlanmış bir dize olabilir. Bazı kültürlerde bu, 1000 olarak yorumlanır, ancak diğer kültürlerde bir noktayı sıfır temsil eder. Yanlış biçimde gerçekleştirilen hesaplamalar ve karşılaştırmalar yanlış veri oluşmasına neden olabilirler.

 Excel dize ile geçilen lcıd 'ye uygun dizeleri yorumlar. Bu, dizenin biçimi geçilen LCıD 'ye karşılık gelmiyorsa bir sorun olabilir. Visual Studio Office geliştirme araçları kullanılarak oluşturulan Excel çözümleri, tüm verileri geçirirken 1033 (en-US) lcıd 'sini kullanın. Excel, verileri bölge ayarlarına ve Excel kullanıcı arabirimi diline göre görüntüler. Visual Basic for Applications (VBA) bu şekilde da çalışmaktadır; dizeler en-US olarak biçimlendirilir ve VBA neredeyse her zaman LCıD olarak 0 (dilden bağımsız) geçirir. Örneğin, aşağıdaki VBA kodu, geçerli kullanıcı yerel ayarlarına uygun olarak 12 Mayıs 2004 için doğru biçimli bir değer görüntüler:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 aynı kod, Visual Studio ' de Office geliştirme araçları kullanılarak oluşturulan ve COM birlikte çalışma üzerinden Excel geçirildiği bir çözümde kullanıldığında, tarih en-US stilinde biçimlendirilirken aynı sonuçları üretir.

 Örnek:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet6":::

 Mümkün olduğunda dize sabit değerleri yerine kesin olarak yazılmış verilerle çalışmanız gerekir. Örneğin, bir tarihi dize değişmez değerinde depolamak yerine, bir olarak depolayın <xref:System.Double> , sonra bunu bir <xref:System.DateTime> işleme için nesnesine dönüştürün.

 Aşağıdaki kod örneği, bir kullanıcının a5 hücresine girdiği bir tarihi alır, onu bir olarak depolar <xref:System.Double> , sonra <xref:System.DateTime> a7 hücresinde görüntülenecek bir nesneye dönüştürür. A7 hücresi bir tarih görüntüleyecek şekilde biçimlendirilmelidir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet7":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet7":::

### <a name="excel-worksheet-functions"></a>Excel çalışma sayfası işlevleri
 Çalışma sayfası işlev adları, Excel dil sürümlerinin çoğu için dahili olarak çevrilir. Ancak, olası dil ve COM birlikte çalışma sorunları nedeniyle kodunuzda yalnızca Ingilizce işlev adları kullanmanız önerilir.

### <a name="applications-that-use-external-data"></a>Dış veri kullanan uygulamalar
 Eski bir sistemden içe aktarılmış, virgülle ayrılmış değerler (CSV dosyaları) içeren dosyalar gibi dış verileri açan ya da başka bir şekilde kullanan herhangi bir kod, bu tür dosyalar, en-US dışında herhangi bir biçim kullanılarak verildiğinde da etkilenebilir. Veritabanı, tarihleri dizeler olarak depoladığından veya ikili biçimi kullanmayan işlemler gerçekleştirmediği sürece, tüm değerlerin ikili biçimde olması gerektiğinden veritabanı erişimi etkilenmeyebilir. ayrıca, Excel verileri kullanarak SQL sorguları oluşturursanız, kullandığınız işleve bağlı olarak bunların en-US biçiminde olduklarından emin olmanız gerekebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: Office çok dilli kullanıcı arabirimini hedefleme](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)