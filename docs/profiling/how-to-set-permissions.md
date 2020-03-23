---
title: 'Nasıl Yapılsın: İzinleri Ayarlama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1ab7705c7ab46b07b08b707ce447f37c581036a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774595"
---
# <a name="how-to-set-permissions"></a>Nasıl yapılsın: İzinleri ayarlama

Bu makalede, bir bilgisayar yöneticisinin, o bilgisayarda Yönetici izinleri olmayan bir kullanıcıya veya gruba profil oluşturma için gereken güvenlik izinlerini nasıl verdiği açıklanmaktadır.

Temel bir güvenlik ilkesi, uygulamaların gereksinim duydukları izinlerden daha fazla çalışmaması gerektiğini belirtir. Bu ilke kullanıcılar için de geçerlidir. Kullanıcılar, Yöneticiler grubu yerine Kullanıcılar grubunun üyeleri olarak oturum açtıklarında tam olarak etkili olabilirlerse, yönetici izni verilmemelidir. "Kullanıcı izinleri olan bir kullanıcı hesabı oluşturmak için" ilk yordam, Kullanıcılar grubunun bir üyesi için nasıl bir kullanıcı hesabı oluşturulacak açıklanır.

Kullanıcılar grubunun üyeleri, takımın diğer üyeleriyle paylaşılan diskteki klasörlere ve dosyalara erişmeye ihtiyaç duyar. İkinci yordam, "Paylaşılan proje dosyalarına erişim vermek için," bu erişim vermek için nasıl açıklar.

Bir yönetici profil oluşturma araçları için yazılım sürücüsüne erişim izni verirse, Kullanıcılar grubunun üyeleri profil oluşturma araçlarını çalıştırabilir. Son yordam, "Profil oluşturma sürücüsüne erişim izni vermek için," bu sürücüye erişim vermek nasıl açıklanır.

> [!NOTE]
> Bu yordamlarda adımları izlemek için yönetici izinleri gerekir.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Kullanıcı izinleri olan bir kullanıcı hesabı oluşturmak için

1. **Bilgisayarım'ı** sağ tıklatın ve ardından **Yönet'i**tıklatın.

     **Bilgisayar Yönetimi** penceresi açılır.

2. **Yerel Kullanıcıları ve Grupları**Genişletin.

3. **Kullanıcılar** klasörüne sağ tıklayın ve ardından **Yeni Kullanıcı'yı**tıklatın.

     **Yeni Kullanıcı** iletişim kutusu görüntülenir.

4. Oluşturduğunuz kullanıcı hesabının bilgileriyle birlikte bu iletişim kutusundaki alanları tamamlayın. Parola belirtin. İsteğe bağlı olarak, kullanıcının bir sonraki oturum açmada parolayı değiştirmesini gerektiren onay kutusunu seçin.

5. **Oluştur'u** tıklatın ve ardından **Kapat'ı**tıklatın.

     Yeni kullanıcı, Yönetici izni olmayan bir kullanıcı grubu olan Kullanıcılar grubunda görünür.

## <a name="to-grant-access-to-shared-project-files"></a>Paylaşılan proje dosyalarına erişim sağlamak için

1. Windows Gezgini'nde (veya Dosya Gezgini'nde), bu kullanıcı tarafından kullanılan ve proje ekibi tarafından paylaşılan proje dosyaları için klasör ağacının kökünü bulun.

     Bu klasörün yolu aşağıdakilere benzeyebilir:

    ```cmd
    D:\ourProject
    ```

2. Klasörü sağ tıklatın ve ardından **Özellikler'i**tıklatın.

     Özellikler iletişim ** \<kutusunun klasör adı>** görüntülenir.

3. **Güvenlik** sekmesine tıklayın.

4. **Grup'taki veya kullanıcı adları** kutusundaki kullanıcı hesabının adını tıklatın.

5. Kullanıcı **adı>\<kutusu için İzinler'de,** **Tam Denetim**için onay kutusunu seçin.

6. **Tamam**'a tıklayın.

     Bu, adım 5'te seçilen klasörle başlayan paylaşılan klasör ağacı için kullanıcıya izin verir.

## <a name="to-grant-access-to-the-profiling-driver"></a>Profil oluşturma sürücüsüne erişim sağlamak için

1. Yönetici olarak bir komut istemi açın.

2. Dizini şu şekilde değiştirin:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Şu komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Bu komut, profil oluşturma araçlarının sürücüsünü yükler ve başlatır.

     Bu komut, yönetici olmayan kullanıcıların Kullanıcı işlem alanında bulunan profil oluşturma özelliklerini kullanabilmeleri için profil oluşturma sürücüsünü ve hizmetini başlatır. Komutu yalnızca bir Yönetici çalıştırabilir; ve yönetim dışı Kullanıcılar için başarısız olur.

     Bu yordamdaki son adımı gerçekleştirmediğiniz sürece, bu adımın etkilerinin bilgisayar yeniden başlatıldıktan sonra geri alınır.

4. Bilgisayara yönetici erişimi olmayan bir kullanıcı veya grup tarafından profil oluşturma sürücüsü işlevselliği erişimine izin vermek için komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Bu komut, \<profil oluşturma \<araçlarına hesap> kullanıcı adı> veya grup adı verir. Sağ \<> seçeneği, kullanıcının erişebileceği profil oluşturma işlevini belirler. Doğru \<> seçeneği aşağıdaki değerlerden biri veya birkaçı olabilir:

    - FullAccess - hizmetlerden performans verileri toplama, örnekleme ve oturumlar arası profil oluşturma dahil olmak üzere tüm profil oluşturma yöntemlerine erişim sağlar.

    - SampleProfiling - örnek profil oluşturma yöntemlerine erişim sağlar

    - CrossSession - profil oluşturma hizmetleri için gerekli olan çapraz oturum profil leme erişimi sağlar.

5. (İsteğe bağlı) Bilgisayar yeniden başlatıldıktan sonra önceki adımlardan herhangi birinin sonuçlarını korumak için aşağıdaki komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Belirtilen kullanıcılar, oturum açtıktan sonra artık yönetici izinleri olmadan profil oluşturma araçlarını kullanabilecekler.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırın[VSPerfCmd](../profiling/vsperfcmd.md)
[Profil Oluşturma ve Windows Vista Güvenliği](../profiling/profiling-and-windows-vista-security.md)
