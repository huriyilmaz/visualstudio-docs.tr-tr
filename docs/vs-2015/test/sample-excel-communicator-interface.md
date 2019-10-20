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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660487"
---
# <a name="sample-excel-communicator-interface"></a>Excel Communicator Arabirimi Örnekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnek `IExcelUICommunication` arabirimi `ExcelAddIn` projesindeki `ExcelUICommunicator` nesnesinde kullanılır.

## <a name="iexceluicommunication-interface"></a>Iexceluicommunication arabirimi
 Bu arabirim, kodlanmış UI test işleminde çalıştırılan `CodedUIExtension` ve [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] işleminde çalışan `ExcelCodedUIAddIn` arasındaki iletişim noktalarını tanımlar.

 @No__t_0 derlemesi Bu arabirimden türetilen bir `ExcelUICommunicator` sınıfına sahiptir ve yöntemleri işlemek için Excel nesne modelini kullanır.

 Bazı yöntemler Excel 'den istenen bilgileri alır ve `CellInformation` nesnesi gibi bilgi nesnelerinden birini oluşturur ve döndürür.

 Diğer yöntemler, belirtilen bir bilgi nesnesini kullanır, Excel 'de ilgili denetimi bulur ve denetimde bazı işlemleri gerçekleştirir. Örneğin `ScrollIntoView` yöntemi, çalışma sayfasını, belirlenen hücrenin görünür olmasını sağlayacak şekilde kaydırır.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample ve ExcelCodedUIAddinHelper Iletişimi
 @No__t_0 derlemesi Excel işleminde çalışır ve `IExcelUITestCommunication` arabirimini uygulayan `UICommunicator` sınıfına sahiptir ve gerekli bilgileri doğrudan Excel kullanıcı arabiriminden alır veya ayarlar.

 @No__t_0 derlemesi, Visual Studio kodlanmış UI test işleminde çalışır. Bu derleme, .NET Remoting kanalını açan `Communicator` sınıfına sahiptir ve istekleri ve bilgi nesnelerini iletmek için `ExcelCodedUIAddinHelper` derlemesinde `UICommunicator` nesnesini kullanmak için `IExcelUICommunication` arabirimini kullanan bir `Instance` özelliği sağlar `CellInformation` nesne gibi iki derleme arasında geri ve ileri.

## <a name="see-also"></a>Ayrıca Bkz.
 Kodlanmış UI testleri için Microsoft Excel [örnek Excel eklentisini](../test/sample-excel-add-in-for-coded-ui-testing.md) [desteklemek Için kodlanmış UI testlerini ve eylem kayıtlarını genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [Excel için kodlanmış UI testi uzantısı örneği](../test/sample-coded-ui-test-extension-for-excel.md)
