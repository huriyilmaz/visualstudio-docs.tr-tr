---
title: Genel sekmesi, Iş parçacığı özellikleri Iletişim kutusu | Microsoft Docs
description: Modül adı, iş parçacığı KIMLIĞI, işlem KIMLIĞI, iş parçacığı durumu, bekleme nedeni ve CPU süresi dahil olmak üzere iş parçacığı hakkında bilgi için Iş parçacığı özellikleri Iletişim kutusunu görüntüleyin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4c2bf24058ce8a69f05d8d2cee17a18ff9505d
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863003"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Genel Sekmesi, İş Parçacığı Özellikleri İletişim Kutusu
Belirli bir iş parçacığı hakkında daha fazla bilgi edinmek için bu iletişim kutusunu kullanın. Bu iletişim kutusunu görüntülemek için odağı bir [Iş parçacığı görünümü](../debugger/threads-view.md) penceresine taşıyın veya [iletiler görünümü](../debugger/messages-view.md) ' ni açın ve bir ileti genişletin. Ağaçta herhangi bir iş parçacığı düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 **Iş parçacığı özellikleri** iletişim kutusu, **genel** sekmesi olan bir bölme içerir. Aşağıdaki ayarlar kullanılabilir:

|Giriş|Description|
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