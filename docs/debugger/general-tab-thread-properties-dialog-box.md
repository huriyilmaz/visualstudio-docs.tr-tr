---
title: Genel Sekme, İş Parçacığı Özellikleri İletişim Kutusu | Microsoft Docs
description: Modül adı, iş parçacığı kimliği, işlem kimliği, iş parçacığı durumu, bekleme nedeni ve CPU süresi gibi bir iş parçacığı hakkında bilgi için İş Parçacığı Özellikleri İletişim Kutusunu görüntüleme.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 30f5fce8a18ec91419c6c81d8c78527e32fd2cc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090830"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Genel Sekmesi, İş Parçacığı Özellikleri İletişim Kutusu
Belirli bir iş parçacığı hakkında daha fazla bilgi için bu iletişim kutusunu kullanın. Bu iletişim kutusunu görüntülemek için odağı bir İş Parçacıkları Görünümü [penceresine](../debugger/threads-view.md) taşının veya İletiler [Görünümü'ne açıp](../debugger/messages-view.md) bir iletiyi genişletin. Ağaçta herhangi bir iş parçacığı düğümünü seçin ve ardından **Görünüm menüsünden** **Özellikler'i** seçin.

 İş **Parçacığı Özellikleri** iletişim kutusunda genel sekmesi olan bir **bölme** vardır. Aşağıdaki ayarlar kullanılabilir:

|Giriş|Açıklama|
|-----------|-----------------|
|**Modül Adı**|Modülün adı.|
|**İş Parçacığı Kimliği**|Bu iş parçacığının benzersiz kimliği. İş parçacığı kimliği numaralarının yeniden kullanılmış olduğunu unutmayın; yalnızca o iş parçacığının ömrü için bir iş parçacığını tanımlamaları gerekir.|
|**İşlem Kimliği**|Bu sürecin benzersiz kimliği. İşlem kimliği numaraları yeniden kullanılır, bu nedenle bir işlemi yalnızca o sürecin ömrü boyunca tanımlamaları gerekir. Bir program çalıştırılan İşlem nesne türü oluşturulur. Bir işlemde yer alan tüm iş parçacıkları aynı adres alanı paylaşır ve aynı verilere erişime sahiptir. İşlem kimliğinin özelliklerini görüntülemek için bu değeri seçin.|
|**İş Parçacığı Durumu**|İş parçacığının geçerli durumu. Çalışan iş parçacığı bir işlemci kullanıyor; Bekleme iş parçacığı bir iş parçacığı kullanmak üzere. Hazır İş Parçacığı, boş bir iş parçacığına sahip olmadığınız için işlemci kullanmayı bekliyor. Geçiş'te bir iş parçacığı, yürütme yığınının diskten diskten diske çağrılmasını beklemek gibi bir kaynağın yürütülmesini bekler. Bekleyen iş parçacığının işlemciye ihtiyacı yok çünkü çevre birimi işleminin tamamlandıktan sonra veya kaynağın serbest bırakılana kadar beklemesi.|
|**Bekleme Nedeni**|Bu yalnızca iş parçacığı Bekleme durumuna geldiğinde geçerlidir. Olay Çiftleri korumalı alt sistemlerle iletişim kurmak için kullanılır.|
|**CPU Süresi**|Bu işlem ve iş parçacıkları için harcanan toplam CPU süresi. Kullanıcı Saati + Ayrıcalıklı Saat'e eşit.|
|**Kullanıcı Saati**|Bu iş parçacığının kullanıcı modunda kod yürütmeye harcadığı toplam süre. Uygulamalar, pencere yöneticisi ve grafik altyapısı gibi alt sistemlerde olduğu gibi Kullanıcı Modunda yürütülür.|
|**Ayrıcalıklı Saat**|Bu iş parçacığının Ayrıcalıklı Mod'da kod yürütmek için harcadığı toplam süre. Bir Windows sistem hizmeti çağrıldı mı, hizmet genellikle ayrıcalıklı modda çalıştırarak sistem özel verilerine erişim elde edin. Bu tür veriler, Kullanıcı Modunda yürütülen iş parçacıkları tarafından erişime karşı korunur. Sisteme yapılan çağrılar açık olabilir veya bir sayfa hatası veya kesinti oluştuğunda olduğu gibi örtülü olabilir.|
|**Geçen Süre**|Bu iş parçacığının geçen toplam süresi (saniye olarak).|
|**Geçerli Öncelik**|Bu iş parçacığının geçerli dinamik önceliği. Bir işlem içindeki iş parçacıkları, sürecin temel önceliğe göre kendi temel önceliklerini yükseltecek ve düşürecek.|
|**Temel Öncelik**|Bu iş parçacığının geçerli temel önceliği.|
|**Başlangıç Adresi**|Bu iş parçacığı için sanal adresi başlatma.|
|**Kullanıcı bilgisayarı**|İş parçacığı için kullanıcı programı sayacı.|
|**Bağlam Anahtarları**|Bir iş parçacığından diğerine geçiş sayısı. İş parçacığı anahtarları tek bir işlem içinde veya işlemler arasında oluşabilir. İş parçacığı anahtarı, bir iş parçacığının başka bir iş parçacığına bilgi istemesi veya daha yüksek öncelikli bir iş parçacığı çalıştırmaya hazır hale geldiğinde bir iş parçacığının önek olması olabilir.|