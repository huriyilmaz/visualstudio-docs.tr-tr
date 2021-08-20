---
title: Kaynak Denetimi Paketleri için Model | Microsoft Docs
description: Bu model bir kaynak denetimi uygulamasını temsil eder. Makale, kaynak denetimin nasıl gerçekleştiril olduğunu daha kolay görmek için sınıfların adlarını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a43d1feb2dde67d6eae291490476db4b98850870
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117871"
---
# <a name="model-for-source-control-packages"></a>Kaynak Denetimi Paketleri için Model
Aşağıdaki model, bir kaynak denetimi uygulaması örneğini temsil eder. Modelde, uygulaması gereken arabirimleri ve çağırma gereken ortam hizmetlerini görüyorsunuz. Tüm hizmetlerde olduğu gibi, hizmetle elde edilen belirli bir arabirimin yöntemlerini çağırabilirsiniz. Kaynak denetimin nasıl gerçekleştirileceklerini daha kolay görmek için sınıfların adları tanımlanır.

 ![SCC&#95;TUP Örnekleri](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Örnek Kaynak Denetimi Project

## <a name="interfaces"></a>Arabirimler
 Aşağıdaki tabloda gösterilen arabirimlerin listesini kullanarak Visual Studio proje türleriniz için kaynak denetimi gerçekleştirebilirsiniz.

|Arabirim|Kullanın|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Dosyaları kaydetmeden veya değiştirmeden önce projeler ve düzenleyiciler tarafından çağrılır. Bu arabirime hizmeti kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bir dosya veya dizin ekleme, kaldırma veya yeniden adlandırma iznini talep etmek için projeler tarafından çağrılır. Bu arabirim, onaylanan bir ekleme, kaldırma veya yeniden adlandırma eylemi tamamlandığında ortamı bilgilendirmek için projeler tarafından da çağrılır. Bu hizmete hizmeti kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeler bir dosya veya dizini ekleyce, yeniden adlandıracak veya kaldıracak şekilde bildirilecek şekilde kaydolan herhangi bir varlık tarafından uygulanır. Olay bildirimine kaydolmak için çağrısına <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> tıklayın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Kaynak denetim paketine kaydolmak ve kaynak denetimi durumu hakkında bilgi almak için projeler tarafından çağrılır. Bu arabirime hizmeti kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> erişilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Proje tarafından, dosyalar hakkında bilgi için kaynak denetim isteklerine yanıt vermek ve proje dosyası için gereken kaynak denetim ayarlarını almak için uygulanır.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
