---
title: 'Örnek Excel uzantısı: ActionFilter sınıfı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672176"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Örnek Excel Uzantısı: ActionFilter Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iç sınıf [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) sınıfını genişletir ve bir öğe üzerindeki test eylemleri için bir filtre temsil eder [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

## <a name="simple-properties"></a>Basit özellikler
 Bu salt okunurdur özellikler, geliştiricinin bu test eylemi filtresinin kodlanmış UI test çerçevesi tarafından nasıl çalıştırılacağını belirtmesini sağlar. Örneğin, `UITestActionFilter.Name` özelliği eylem filtresinin adını sağlar. Diğer özellikler, `UITestActionFilter.Category` `UITestActionFilter.FilterType` `UITestActionFilter.Group` Bu test eylemi filtresi tarafından filtrelenen test eylemlerinin adını, eylem filtresinin, bu adı alır. Diğer kişiler `UITestActionFilter.ApplyTimeout` de test eyleminin olup olmadığını gösterir `UITestActionFilter.Enabled` .

## <a name="processrule-method"></a>ProcessRule yöntemi
 Bu yöntem, kodlanmış UI test çerçevesi tarafından çağrılır ve filtreyi belirtilen şekilde yürütür `IUITestActionStack` . Bu özel geçersiz kılma, yığındaki bir sonraki eylem, hücreye tuş vuruşları gönderdiğinde bir hücrede fare seçme eylemini kaldırır. Ardından döndürür `false` .

## <a name="private-methods"></a>Özel Yöntemler
 `IsLeftClick`Yöntemi, belirtilen eylemin farenin sol tıklamasını temsil ettiğini belirler. `AreActionsOnSameExcelCell`Yöntemi, Excel 'deki aynı hücrede iki adet belirtilen eylemin yürütülüp yürütülmeyeceğini belirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
