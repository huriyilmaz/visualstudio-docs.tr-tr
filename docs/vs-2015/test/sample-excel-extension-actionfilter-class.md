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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672176"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Örnek Excel Uzantısı: ActionFilter Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iç sınıf [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) sınıfını genişletir ve bir [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] öğesinde test eylemleri için bir filtre temsil eder.

## <a name="simple-properties"></a>Basit özellikler
 Bu salt okunurdur özellikler, geliştiricinin bu test eylemi filtresinin kodlanmış UI test çerçevesi tarafından nasıl çalıştırılacağını belirtmesini sağlar. Örneğin, `UITestActionFilter.Name` özelliği eylem filtresinin adını sağlar. Diğer özellikler, eylem filtresinin `UITestActionFilter.Category`, `UITestActionFilter.FilterType`, bu test eylemi filtresi tarafından filtrelenen test eylemlerinin `UITestActionFilter.Group` adını alır. Diğerleri, `UITestActionFilter.ApplyTimeout` ve ayrıca test eyleminin `UITestActionFilter.Enabled` olup olmadığını gösterir.

## <a name="processrule-method"></a>ProcessRule yöntemi
 Bu yöntem, kodlanmış UI test çerçevesi tarafından çağrılır ve bu filtre, belirtilen `IUITestActionStack` karşı yürütülür. Bu özel geçersiz kılma, yığındaki bir sonraki eylem, hücreye tuş vuruşları gönderdiğinde bir hücrede fare seçme eylemini kaldırır. Ardından `false` döndürür.

## <a name="private-methods"></a>Özel Yöntemler
 @No__t_0 yöntemi, belirtilen eylemin farenin sol tıklamasını temsil ettiğini belirler. @No__t_0 yöntemi, Excel 'deki aynı hücrede iki adet belirtilen eylemin yürütülüp yürütülmeyeceğini belirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
