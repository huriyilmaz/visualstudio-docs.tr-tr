---
title: Genel sekmesi, Iş parçacığı özellikleri Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b1a8e6fd583f6035fc84f0c86adcee059562235d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159950"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Genel Sekmesi, İş Parçacığı Özellikleri İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli bir iş parçacığı hakkında daha fazla bilgi edinmek için bu iletişim kutusunu kullanın. Bu iletişim kutusunu görüntülemek için odağı bir [Iş parçacığı görünümü](../debugger/threads-view.md) penceresine taşıyın veya [iletiler görünümü](../debugger/messages-view.md) ' ni açın ve bir ileti genişletin. Ağaçta herhangi bir iş parçacığı düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.  
  
 **Iş parçacığı özellikleri** iletişim kutusu, **genel** sekmesi olan bir bölme içerir. Aşağıdaki ayarlar kullanılabilir:  
  
|Giriş|Açıklama|  
|-----------|-----------------|  
|**Modül Adı**|Modülün adı.|  
|**İş parçacığı KIMLIĞI**|Bu iş parçacığının benzersiz KIMLIĞI. İş parçacığı KIMLIĞI numaralarının yeniden kullanılabilir olduğunu unutmayın. bir iş parçacığını yalnızca o iş parçacığının ömrü için tanımlarlar.|  
|**İşlem Kimliği**|Bu işlemin benzersiz KIMLIĞI. İşlem KIMLIĞI numaraları yeniden kullanılır, bu nedenle bir işlemi yalnızca bu işlemin kullanım ömrü için tanımlarlar. Işlem nesnesi türü, bir program çalıştırıldığında oluşturulur. Bir işlemdeki tüm iş parçacıkları aynı adres alanını paylaşır ve aynı verilere erişebilir. İşlem KIMLIĞININ özelliklerini görüntülemek için bu değeri seçin.|  
|**İş parçacığı durumu**|İş parçacığının geçerli durumu. Çalışan bir iş parçacığı işlemciyi kullanıyor; bir bekleme iş parçacığı kullanmak için. Ücretsiz bir Iş parçacığı, bir işlemcinin kullanılmasını bekliyor çünkü bir işlem ücretsizdir. Geçiş içindeki bir iş parçacığı, yürütme yığınının diskten disk belleğine alınması beklendiğinden bir kaynağın yürütülmesini bekliyor. Bir çevre birimi işleminin tamamlanmasını veya bir kaynağın ücretsiz olmasını beklediği için bekleyen bir iş parçacığı işlemciyi gerektirmez.|  
|**Bekleme nedeni**|Bu, yalnızca iş parçacığı bekleme durumundayken geçerlidir. Olay çiftleri, korumalı alt sistemler ile iletişim kurmak için kullanılır.|  
|**CPU süresi**|Bu işlem ve iş parçacıkları üzerinde harcanan toplam CPU süresi. Kullanıcı zamanına ve ayrıcalıklı zamana eşit.|  
|**Kullanıcı saati**|Bu iş parçacığının kullanıcı modunda kod çalıştırırken harcadığı toplam geçen süre. Uygulamalar, pencere yöneticisi ve grafik altyapısı gibi alt sistemler gibi kullanıcı modunda yürütülür.|  
|**Ayrıcalıklı zaman**|Bu iş parçacığının ayrıcalıklı modda kod çalıştırırken harcadığı toplam geçen süre. Bir Windows sistem hizmeti çağrıldığında hizmet genellikle ayrıcalıklı modda çalışır ve sistem özel verilerine erişim elde edilir. Bu tür veriler, kullanıcı modunda çalışan iş parçacıklarının erişimine karşı korunur. Sisteme yapılan çağrılar açık olabilir veya bir sayfa hatası ya da kesme gerçekleştiğinde örtük olabilir.|  
|**Geçen süre**|Bu iş parçacığının çalıştığı toplam geçen süre (saniye cinsinden).|  
|**Geçerli öncelik**|Bu iş parçacığının geçerli dinamik önceliği. Bir işlem içindeki iş parçacıkları, işlemin temel önceliğine göre kendi temel önceliklerini artırıp düşürebilirler.|  
|**Temel öncelik**|Bu iş parçacığının geçerli temel önceliği.|  
|**Başlangıç adresi**|Bu iş parçacığının sanal adresi başlatılıyor.|  
|**Kullanıcı bılgısayar**|İş parçacığı için Kullanıcı programı sayacı.|  
|**Bağlam geçişleri**|Bir iş parçacığından diğerine anahtar sayısı. İş parçacığı anahtarları, tek bir işlem içinde veya işlemler arasında gerçekleşebilir. İş parçacığı anahtarı, daha fazla bilgi isteyen bir iş parçacığından veya daha yüksek öncelikli bir iş parçacığı çalıştırılmaya hazır olduğunda bir iş parçacığı tarafından neden olmuş olabilir.|
