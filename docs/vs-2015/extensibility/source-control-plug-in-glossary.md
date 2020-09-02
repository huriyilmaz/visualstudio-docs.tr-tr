---
title: Kaynak denetimi eklentisi sözlüğü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160600"
---
# <a name="source-control-plug-in-glossary"></a>Kaynak Denetimi Eklentisi Sözlüğü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki faydalı hüküm ve tanımlar, kaynak denetimi eklentisi SDK belgeleriyle ilgilidir.  
  
## <a name="definitions"></a>Tanımlar  
 In  
 Bir Kullanıcı bir çalışma kopyasında değişiklik yaptığında, kullanıcının değişiklikleri çalışma kopyasından merkezi kaynak denetimi deposuna gönderebilmesi gerekir. Bu, dosyanın diğer kullanıcılar tarafından kullanılabilen yeni bir düzeltmesini oluşturur. Bu işleme iade adı verilir.  
  
 Kullanıma alma  
 Depodan, değişiklik yapma amacınızı bildiren bir çalışma kopyası isteme eylemi. Çalışma kopyası, projenin durumunu kullanıma alındığı andan itibaren yansıtır.  
  
 İstemci  
 Kaynak kodu denetim sistemini kullanan bir program. Bu belgelerin amacına yönelik olarak, Visual Studio IDE 'dir.  
  
 Yorum  
 Bir kaynak denetim işlemi gerçekleştirildiğinde, bir kullanıcının düzeltmeye iliştireme yaptığı değişiklikleri açıklayan bir ileti.  
  
 Çakışma  
 İki kullanıcı aynı dosyanın aynı bölgesindeki değişiklikleri iade etmek denediğinde bir durum. Genellikle, bir birleştirme gerçekleştirilmelidir.  
  
 Dizin  
 Bir istemci tarafı yerel klasörü, dizin olarak adlandırılır. Bu, kullanıcının aslında değişiklik yaptığı kopyasıdır. Belirli bir projenin birçok çalışma kopyası olabilir; genellikle her geliştiricinin kendi kopyası vardır.  
  
 Al  
 Bir get işlemi kullanıcının çalışma kopyasını depo kopyasıyla güncel hale getirir. Bir kullanıma almanın aksine, Kullanıcı yalnızca en son kopyaya ihtiyaç duymadığında ancak hiçbir değişiklik yapmadan bir alma işlemi gerçekleştirilir.  
  
 Geçmiş  
 Genellikle kaynak denetim deposunda yapılan tüm kullanıma alma işlemleri, iadeler, güncelleştirmeler, Etiketler ve sürümlerin bir özetidir.  
  
 IDE  
 Genellikle Visual Studio tümleşik geliştirme ortamına başvurur. Ancak, kaynak denetimi eklentisi API 'sini tanıyan diğer istemci ortamlarına de başvurabilir.  
  
 Birleştir  
 Önceki dosyalardaki tüm özellikleri içeren yeni bir dosya oluşturmak için iki veya daha fazla kaynak kodu dosyasının birleştirileceği işlem. Bu kavram, iki veya daha fazla geliştiricinin dosyalarda eşzamanlı olarak çalıştığı sürüm denetiminde hayati öneme sahiptir.  
  
 Project  
 Kaynak denetim klasörü genellikle proje olarak adlandırılır. Bu, Visual Studio 'daki proje veya çözümlerle hiçbir ilişkiye sahip değildir.  
  
 Eklenti  
 Kaynak denetimi eklentisi API 'sini uygulayarak kaynak denetimi işlevselliği sağlayan bir DLL.  
  
 Depo  
 Kaynak denetim sisteminin bir projenin tam değişiklik geçmişini sakladığı ana kopya. Her projenin tam olarak bir deposu vardır.  
  
 Revizyon  
 Bir dosya veya dosya kümesinin geçmişinde yürütülen değişiklik. Bir düzeltme, sürekli değişen bir projede bir anlık görüntüdür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
