---
title: IDE tarafından uygulanan geri çağırma Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: df2daef11303e85d5fe2d0bf33e3df038081db64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184528"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE Tarafından Uygulanan Geri Çağırma İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tümleşik geliştirme ortamı (IDE) ile tümleştirmeyi mümkün olduğunca sorunsuz hale getirmek ve birleştirilmiş bir son kullanıcı deneyimi sağlamak için, kaynak denetimi eklentisi IDE tarafından uygulanan geri çağırma işlevlerini kullanabilir. Eklenti, IDE 'ye bilgi geçirmek için kaynak denetim işlemi sırasında bu işlevleri uygun zamanlarda çağırabilir; IDE daha sonra bu bilgileri yerel kullanıcı arabiriminde katıştırılmış öğeler olarak görüntüleyebilir. Bu senaryoda, eklenti kendi Kullanıcı arabirimini işe alıyorsa, kullanıcının bu senaryoda daha az parçalanmış bir deneyimi vardır.  
  
 Gerekli üst bilgi dosyası SCC. h ' dir. Varsayılan konum \Program Files\vsıp 8.0 \ EnvSDK\common\inc ' dir \\ . Ayrıca, \Program Files\vsıp 8.0 \ MSSCCı konumundaki kaynak denetimi eklentisi örneğine sahip VSıP klasöründedir \\ .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 IDE aracılığıyla kaynak denetimi eklentisindeki iletileri göstermek için [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılan geri çağırma işlevini açıklar.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 IDE 'nin yalnızca kaynak denetimi eklentisi için kullanılabilir olan bilgilere (sürüm denetimi altındaki tam bir liste gibi) tam erişimi olmadığında, [SccPopulateList](../extensibility/sccpopulatelist-function.md) tarafından kullanılan geri çağırma işlevini açıklar.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından kullanılan geri çağırma işlevini açıklar.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlemi tarafından kullanılan geri çağırma işlevini açıklar.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Kaynak denetimi eklentisinin IDE 'ye yeniden iletişim kurmasını sağlayan [SccSetOption](../extensibility/sccsetoption-function.md) çağrısı tarafından ayarlanan geri çağırma işlevini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Bir proje açar.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Geçerli durumları için dosya listesini inceler. Ayrıca, `pfnPopulate` bir dosya ile ilgili ölçütlerle eşleşmediği zaman, çağrıyı yapana bildirmek için işlevini kullanır `nCommand` .  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Kaynak denetimi altındaki bir projedeki veya projelerdeki dizinlerin ve dosyaların listesini inceler. Bulunan her dizin ve dosya adı bir geri çağırma işlevine geçirilir.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Dosya listesinde yapılan ad değişikliklerini inceler. Her dosya adı, değişiklik durumuyla birlikte bir geri çağırma işlevine geçirilir.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Çok çeşitli seçenekler ayarlar. Her seçenek ile başlar `SCC_OPT_xxx` ve kendi tanımlı değer kümesine sahiptir.  
  
 [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)  
 Kaynak denetimi eklentisi SDK 'sının başvuru bölümünün içeriğini açıklar.
