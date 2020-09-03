---
title: Örnek Excel Communicator Arabirimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660487"
---
# <a name="sample-excel-communicator-interface"></a>Excel Communicator Arabirimi Örnekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnek `IExcelUICommunication` arabirim, `ExcelUICommunicator` projedeki nesnesinde kullanılır `ExcelAddIn` .

## <a name="iexceluicommunication-interface"></a>Iexceluicommunication arabirimi
 Bu arabirim, `CodedUIExtension` KODLANMıŞ UI test işleminde çalıştırılan ve işleminde çalışan, arasındaki iletişim noktalarını tanımlar `ExcelCodedUIAddIn` [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

 `ExcelCodedUIAddinHelper`Derlemenin `ExcelUICommunicator` Bu arabirimden türeten bir sınıfı vardır ve yöntemleri Işlemek için Excel nesne modelini kullanır.

 Bazı yöntemler Excel 'den istenen bilgileri alır, ardından nesne gibi bilgi nesnelerinden birini oluşturur ve döndürür `CellInformation` .

 Diğer yöntemler, belirtilen bir bilgi nesnesini kullanır, Excel 'de ilgili denetimi bulur ve denetimde bazı işlemleri gerçekleştirir. Örneğin, yöntemi, `ScrollIntoView` belirlenen hücrenin görünür olması Için çalışma sayfasını kaydırır.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample ve ExcelCodedUIAddinHelper Iletişimi
 `ExcelCodedUIAddinHelper`Derleme Excel işleminde çalışır ve `UICommunicator` arabirimi uygulayan sınıfına sahiptir `IExcelUITestCommunication` ve gerekli bilgileri doğrudan Excel kullanıcı arabiriminden alır veya ayarlar.

 `CodedUIExtensibilitySample`Derleme, Visual Studio KODLANMıŞ UI test işleminde çalışır. Bu derleme `Communicator` .NET uzaktan iletişim kanalı açan sınıfa sahiptir ve `Instance` `IExcelUICommunication` `UICommunicator` `ExcelCodedUIAddinHelper` bir nesne gibi istekleri ve bilgi nesnelerini `CellInformation` iki derleme arasında ileri ve geri geçirmek için derleme içindeki nesnesini kullanmak üzere arabirimini kullanan bir özellik sağlar.

## <a name="see-also"></a>Ayrıca Bkz.
 Kodlanmış UI testleri için Microsoft Excel [örnek Excel eklentisini](../test/sample-excel-add-in-for-coded-ui-testing.md) [desteklemek Için kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [Excel için kodlanmış UI testi uzantısı örneği](../test/sample-coded-ui-test-extension-for-excel.md)
