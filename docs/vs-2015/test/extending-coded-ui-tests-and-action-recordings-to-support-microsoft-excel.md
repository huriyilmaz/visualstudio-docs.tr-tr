---
title: Microsoft Excel 'i desteklemek için kodlanmış UI testlerini ve eylem kayıtlarını genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4cac9981a582d5ba9527e0f8dc47d14b6fba18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851761"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri ve eylem kayıtları için test çerçevesi, olası her kullanıcı arabirimini desteklemez. Test etmek istediğiniz belirli kullanıcı arabirimini desteklemiyor olabilir. Örneğin, bir elektronik tablo için hemen kodlanmış UI testi veya eylem kaydı oluşturamazsınız [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] . Ancak, kodlanmış UI test çerçevesinin genişletilebilirliğine katılarak, kodlanmış UI test çerçevesi için kendi uzantınızı oluşturabilirsiniz. Aşağıdaki konu, için kodlanmış UI testleri ve eylem kayıtlarının oluşturulmasını desteklemek için çerçevesini genişletmenin bir örneğini vermektedir [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] . Desteklenen platformlar hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri ve eylem kayıtları Için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

 **Gereksinimler**

- Visual Studio Enterprise

  Bu bölüm, Excel çalışma sayfalarına yönelik testleri kaydedebilve kayıttan oynatacak kodlanmış bir UI testi uzantısı sunar. Uzantının her bölümü, bu bölümde ve yalnızca böyle bir uzantıyı oluşturmak isteyen geliştiriciler için kod açıklamalarında açıklanmıştır.

  ![UI test mimarisi](../test/media/ui-testarch.png "UI_TestArch") Mimariye genel bakış

## <a name="download-the-sample"></a>Örneği indirme
 Örnek, çözümdeki dört projeden oluşur `CodedUIExtensibilitySample.sln` :

- CodedUIextensibilitySample

- ExcelCodedUIAddInHelper

- Exceluıicommunicationhelper

- SampleTestProject

  Bu [blog gönderisine](https://blogs.msdn.com/b/gautamg/archive/2010/01/05/3-introducing-sample-excel-extension.aspx)örnek alın.

> [!NOTE]
> Örnek, Microsoft Excel 2010 ile kullanılmak üzere tasarlanmıştır. Örnek, Microsoft Excel 'in diğer sürümleriyle çalışabilir, ancak şu anda desteklenmemektedir.

## <a name="details-about-the-sample"></a>Örnekle ilgili ayrıntılar
 Aşağıdaki bölümlerde örnek ve yapısı hakkında bilgi sağlanmaktadır.

### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Microsoft Excel eklentisi: ExcelCodedUIAddinHelper
 Bu proje, Excel işleminde çalışan bir eklenti içerir. Eklenti projesine kısa bir genel bakış için bkz. [KODLANMıŞ UI testi Için örnek Excel eklentisi](../test/sample-excel-add-in-for-coded-ui-testing.md) .

 Daha fazla bilgi için bkz. [Izlenecek yol: Excel Için Ilk VSTO eklentisini oluşturma](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).

### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Excel UI iletişimi: Exceluıicommunicationhelper
 Bu proje, `IExcelUICommunication` KODLANMıŞ UI test çerçevesi ve Excel arasında veri geçirmek için kullanılan arabirimi ve bilgi sınıflarını içerir. Daha fazla bilgi için bkz. [örnek Excel Communicator Arabirimi](../test/sample-excel-communicator-interface.md).

### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Kodlanmış UI test uzantısı: CodedUIExentsibilitySample
 Bu proje, bir Excel çalışma sayfası testlerinde kullanılan özel sınıfları içerir. Bu sınıfların her biri için kod oldukça kendi kendine açıklayıcıdır. Ancak, her bir özel sınıfın kısa bir açıklamasını sağlıyoruz. Daha fazla bilgi için bkz. [Excel Için örnek KODLANMıŞ UI testi uzantısı](../test/sample-coded-ui-test-extension-for-excel.md).

### <a name="deploying-your-add-in-and-extension"></a>Eklentiyi ve uzantınızı dağıtma
 Tüm projeleri ve nesneleri oluşturduktan sonra, sağlanmış `CopyDrop.bat` dosyayı yönetici olarak çalıştırın. Bu dosya `ExcelCodedUIAddinHelper` dll ve PDB dosyalarını şu şekilde kopyalar:

 " `%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*` ", sürüm numarası 11,0, 12,0, Visual Studio sürümünüzü temel alır.

 `ExcelUICommunicationHelper`Dll ve pdb dosyaları ' ye kopyalanır `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”` .

 Tam kopyalama yollarını ayarlamanız gerekebilir, ancak ek yükleme gerekmez. 64 bitlik bir makinede, dosyayı çalıştırmak için 32-bit Visual Studio Enterprise komut istemi ' ni kullanın `CopyDrop.bat` .

### <a name="testing-excel-with-the-sampletestproject"></a>SampleTestProject ile Excel 'i test etme
 Excel 'in sahip olmadığınız belirli bir sürümünü kullanan belirtilen test projesinde testi çalıştırabilir ya da kendi test projenizi oluşturabilir ve kendi test projenize bir test kaydedebilirsiniz. Daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI Testleri için En İyi Yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
