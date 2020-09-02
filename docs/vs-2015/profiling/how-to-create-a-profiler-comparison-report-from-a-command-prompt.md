---
title: 'Nasıl yapılır: komut Isteminden profil oluşturucu karşılaştırma raporu oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179575"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Nasıl yapılır: Komut İsteminden Profil Oluşturucu Karşılaştırma Raporu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]İki profil oluşturma verisinin performans verilerini karşılaştıran bir profil oluşturma araçları raporu oluşturabilirsiniz (. VSP/or. VSPS) dosyaları. Rapor, bir profil oluşturma oturumundan diğerine gerçekleşen farkları, performans gerilemeleri ve geliştirmeleri gösterir. Rapordaki değerler, belirttiğiniz ilk dosyanın taban çizgisinden Delta veya değişiklik sunar. Bu Delta, taban çizgisi değeri olan eski değer ve yeni analizin sonucu değeri arasındaki farkı belirleyerek hesaplanır. Profiler verilerinin karşılaştırmaları, koddaki işlevlere, uygulamadaki modüllerde, satırlarda, yönerge işaretçilerine (IP) ve türlere göre yapılabilir.  
  
 Karşılaştırma kategorilerinin ve alanlarının tanımlayıcılarını listelemek için aşağıdaki komut satırını yazın:  
  
 **VSPerfReport/querydifftables**  *VspFileName1* *VspFileName2*  
  
 Karşılaştırma raporu oluşturmak için aşağıdaki sözdizimini kullanın:  
  
 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]    
  
 Aşağıdaki tablodan **VSPerfReport/diff** komut satırına seçenekler ekleyebilirsiniz.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Diffthreshold:**[*değer*]|Bu yüzde eşik değerinin altındaysa farkı dikkate almaz. Ayrıca, bu eşiğin altındaki değerlere sahip olan yeni veriler görünmez.|  
|**Difftable:** *TableName*|Dosyaları karşılaştırmak için bu tabloyu kullanın. Varsayılan olarak, işlevler tablosu kullanılır. **VSPerfReport/querydifftables**içinde listelenen tanımlayıcıyı belirtin.|  
|**Diffcolumn:** *ColumnName*|Değerleri karşılaştırmak için bu sütunu kullanın. Varsayılan olarak, dışlayıcı örnek yüzdesi sütunu kullanılır. **VSPerfReport/querydifftables**içinde listelenen tanımlayıcıyı belirtin.|
