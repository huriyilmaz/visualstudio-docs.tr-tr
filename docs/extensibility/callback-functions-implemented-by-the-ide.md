---
title: IDE tarafından uygulanan geri arama fonksiyonları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739898"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE tarafından uygulanan geri arama işlevleri
Tümleşik geliştirme ortamıyla (IDE) mümkün olduğunca sorunsuz bir tümleştirme yapmak ve birleşik bir son kullanıcı deneyimi sağlamak için kaynak denetim eklentisi IDE tarafından uygulanan geri arama işlevlerini kullanabilir. Eklenti, bilgi nin IDE'ye iletilmesi için kaynak kontrol işlemi sırasında bu işlevleri uygun zamanlarda arayabilir; IDE daha sonra bu bilgileri yerel Kullanıcı Bira'sında gömülü öğeler olarak görüntüleyebilir. Kullanıcı, eklentinin kendi kullanıcı arasını çalıştırdığı ndan daha az parçalanmış bir deneyime sahiptir.

 Gerekli üstbilgi dosyası *scc.h.* Varsayılan konum *\Program Dosyaları\VSIP 8.0\EnvSDK\common\inc.\\* Ayrıca *\Program Files\VSIP 8.0\MSSCCI\\*adresinde kaynak denetimi eklentisi örneğine sahip VSIP klasöründedir.

## <a name="in-this-section"></a>Bu bölümde
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) IDE aracılığıyla kaynak denetim eklentisinden gelen iletileri görüntülemek için [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılan geri arama işlevini açıklar.

- [POPLISTFUNC](../extensibility/poplistfunc.md) IDE, sürüm denetimi altındaki dosyaların tam listesi gibi yalnızca kaynak denetim eklentisi tarafından kullanılabilen bilgilere tam erişime sahip olmadığında [SccPopulateList](../extensibility/sccpopulatelist-function.md) tarafından kullanılan geri arama işlevini açıklar.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi tarafından kullanılan geri arama işlevini açıklar.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlemi tarafından kullanılan geri arama işlevini açıklar.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) [SccSetOption'a](../extensibility/sccsetoption-function.md) yapılan bir çağrıyla ayarlanan geri arama işlevini açıklar ve kaynak denetim eklentisinin ad değişikliklerini IDE'ye geri iletmesini sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [SccOpenProject](../extensibility/sccopenproject-function.md) Bir proje açar.

- [SccPopulateListesi](../extensibility/sccpopulatelist-function.md) Geçerli durumları için dosyaların listesini inceler. Buna ek olarak, bir dosya için ölçütleri eşleşmiyor zaman arayan bildirmek için `pfnPopulate` işlevi `nCommand`kullanır.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Kaynak denetimi altında olan proje veya projelerdeki dizin ve dosyaların listesini inceler. Bulunan her dizin ve dosya adı bir geri arama işlevine geçirilir.

- [SccQueryDeğişiklikler](../extensibility/sccquerychanges-function.md) Dosya listesinde yapılan ad değişikliklerini inceler. Her dosya adı, değiştirme durumuyla birlikte bir geri arama işlevine aktarılır.

- [SccSetOption](../extensibility/sccsetoption-function.md) Çok çeşitli seçenekler belirler. Her seçenek `SCC_OPT_xxx` ile başlar ve kendi tanımlanmış değerler kümesi vardır.

- [Kaynak Kontrol Eklentileri](../extensibility/source-control-plug-ins.md) Kaynak Denetim Eklentisi SDK'nın referans bölümünün içeriğini açıklar.
