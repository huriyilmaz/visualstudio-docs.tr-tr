---
title: Kodlanmış UI testi için Excel Eklentisi örneği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6dc6b4385130c6341b5b3545c6c9f71dc67457f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672193"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Kodlanmış UI Testi için Excel Eklenti Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçin bu örnek eklenti [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] , Visual Studio Enterprise kaydedilen ve çalıştırılan Excel çalışma sayfalarının KODLANMıŞ UI testlerini desteklemek için özel olarak tasarlanmıştır. Eklenti, Office için Visual Studio Araçları kullanılarak oluşturulur.

 Excel eklentisi oluşturma hakkında daha fazla bilgi için bkz. [Izlenecek yol: Excel Için Ilk VSTO eklentisini oluşturma](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) veya "Excel eklentisi" için MSDN arama.

 Excel eklentisi Excel için kodlanmış UI testi uzantısının bu belgelerinin birincil konusu olmasa da birkaç açıklama yararlı olabilir.

 Bu eklentinin önemli kısımları:

- `ThisAddIn`  Sınıf- `ExcelUICommunicator` [Excel Için ve örnek kodlanmış UI testi uzantısı](../test/sample-coded-ui-test-extension-for-excel.md)arasındaki .NET uzaktan iletişim kanalını yönetir.

- `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  -Eklentiyi test etmek için bir güvenlik sertifikası.

- `ExcelUICommunicator`  Sınıf-bu sınıf, `IExcelUICommunication` arabirimini uygular.

## <a name="thisaddin-class"></a>ThisAddIn sınıfı
 Bu sınıfın çoğu aslında, `ThisAddIn.Designer.cs` Excel eklenti projenizi oluştururken dosyada Office için Visual Studio Araçları tarafından oluşturulur.

 Uygulamanız gereken Üyeler olay işleyicileridir: `ThisAddIn_Startup()` ve `ThisAddIn_Shutdown()` . Amaçları, tarafından kullanılan .NET uzaktan Iletişim kanalını başlatma veya kapatma amaçlıdır `ExcelUICommunicator` .

## <a name="excelcodeduiaddinhelper_temporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey. pfx
 Bu dosya, Office için Visual Studio Araçları tarafından oluşturulan geçici bir güvenlik sertifikası içerir ve eklenti derleme iznini, eklentiyi ve uzantıyı test etmek için Excel işleminde çalışmaya olanak sağlar. Bu sertifikayı silmeli ve proje **özellikleri** penceresinin **imzalama** sekmesinde yeni bir tane oluşturmanız ya da kendi test sertifikanızı eklemeniz gerekir.

## <a name="exceluicommunicator-class"></a>Exceluıicommunicator sınıfı
 Bu sınıf, `IExcelUITestCommunication` arabirimini uygular ve istenen kullanıcı arabirimi bilgilerini Excel nesne modelinden alır. Daha fazla bilgi için bkz. [örnek Excel Communicator Arabirimi](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Microsoft Excel gözden geçirmeyi desteklemek Için KODLANMıŞ UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) : Excel [Office ve SharePoint GELIŞTIRME](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329) [için ilk VSTO eklentisini oluşturma](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)
