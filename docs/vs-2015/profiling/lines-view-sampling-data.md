---
title: Satırlar Görünümü-Örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2e5511e9e2e1c863db8f696a70195573d75429f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832956"
---
# <a name="lines-view---sampling-data"></a>Satırlar Görünümü - Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme verilerinin satırlar görünümü, profil oluşturma çalıştırmasında örnek toplandığında yürütülen deyimler için performans verilerini listeler.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Bir kaynak dosyasında, bir ifade kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla ifade içerebilir. Bir ifade aşağıdaki şekilde tanımlanır:  
  
- Function ifadesini içeren kaynak dosya.  
  
- İfadesini içeren işlev.  
  
- Deyimin başladığı kaynak satır.  
  
- Deyimin başladığı kaynak satırdaki karakter.  
  
- Deyimin bittiği kaynak satır.  
  
- Deyimin bittiği kaynak satırdaki karakter.  
  
  Satır adı sütunu, tanımlayıcı verilerinin sıralanabilir bir birleştirmesini sağlar.  
  
  Tanım olarak, bir ifade diğer işlevleri çağırmaz. Bu nedenle, yalnızca dışlamalı değerler listelenir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlev satırını içeren modülün adı.|  
|**Modül yolu**|İşlev satırını içeren modülün yolu.|  
|**Kaynak Dosya**|İşlev satırını içeren kaynak dosya.|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**İşlev adresi**|İşlevin başlangıç adresi.|  
|**Kaynak satırı başlangıç**|Bu örneğin toplandığı kaynak dosyadaki başlangıç satırı numarası.|  
|**Kaynak satır sonu**|Bu örneğin toplandığı kaynak dosyadaki bitiş satırı numarası.|  
|**Kaynak karakter başlangıcı**|Bu örneğin toplandığı kaynak dosya satırındaki başlangıç karakterinin boşluğu.|  
|**Kaynak karakter sonu**|Bu örneğin toplandığı kaynak dosya satırındaki bitiş karakterinin boşluğu.|  
|**Satır adı**|Aşağıdaki sözdizimine sahip satır için profil oluşturucu tarafından oluşturulan bir tanımlayıcı: `Source File` **; [** `Line Number Start` **,**`Character Start` **]->; [**`Line Number End`**,**`Character End`**]**|  
|**Dışlamalı örnekler**|İşlev satırı yürütüldüğü zaman toplanan örneklerin toplam sayısı.|  
|**Dışlamalı örnekler%**|İşlev satırı yürütüldüğü sırada toplanan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Satırlar Görünümü - Örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
