---
title: İzinleri | Microsoft Docs
description: Bir bilgisayarın Yöneticisinin, Yönetici izinlerine sahip bir kullanıcıya veya gruba profil oluşturma için gereken güvenlik izinlerini nasıl verir?
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 56dee60e63ce2f6d3d298c3c70e57f59910a16ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150228"
---
# <a name="how-to-set-permissions"></a>Nasıl ayarlanır: İzinleri ayarlama

Bu makalede, bir bilgisayarın Yöneticisinin profil oluşturma için gereken güvenlik izinlerini, o bilgisayarda Yönetici izinlerine sahip değil bir kullanıcıya veya gruba nasıl izni olduğu açıklanmıştır.

Temel bir güvenlik ilkesi, uygulamaların ihtiyaç fazlası olan izinlerle çalışması gerektiğini ifade ediyor. Bu ilke kullanıcılar için de geçerlidir. Kullanıcılar Yöneticiler grubu yerine Kullanıcılar grubunun üyesi olarak oturum açtıklarına göre tam olarak etkili olabilirse, bu kullanıcılara Yönetici izinleri verilmez. İlk yordam olan "Kullanıcı izinlerine sahip bir kullanıcı hesabı oluşturmak için", Kullanıcılar grubunun bir üyesi için bir kullanıcı hesabının nasıl oluşturularak ilgili açıklamayı içerir.

Kullanıcılar grubunun üyelerinin, disk üzerinde ekibin diğer üyeleriyle paylaşılan klasörlere ve dosyalara erişmesi gerekir. İkinci yordam olan "Paylaşılan proje dosyalarına erişim izni vermek için" bu erişimin nasıl verilmesini açıklar.

Bir yönetici profil oluşturma araçları için yazılım sürücüsüne erişim izni verdiyseniz Kullanıcılar grubunun üyeleri profil oluşturma araçlarını çalıştırabilirsiniz. Son yordam olan "Profil oluşturma sürücüsüne erişim izni vermek için" bu sürücüye nasıl erişim ver ver windows.

> [!NOTE]
> Bu yordamlarda verilen adımları takip etmek için yönetici izinlerine ihtiyacınız vardır.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Kullanıcı izinlerine sahip bir kullanıcı hesabı oluşturmak için

1. Bilgisayarım'a **sağ tıklayın ve** ardından Yönet'e **tıklayın.**

     Bilgisayar **Yönetimi penceresi** açılır.

2. Yerel **Kullanıcılar ve Gruplar'a genişletin.**

3. Kullanıcılar klasörüne **sağ tıklayın** ve ardından Yeni Kullanıcı'ya **tıklayın.**

     Yeni **Kullanıcı iletişim** kutusu görüntülenir.

4. Bu iletişim kutusundaki alanları, oluşturmakta olan kullanıcı hesabının bilgileriyle doldurun. Bir parola belirtin. İsteğe bağlı olarak, kullanıcının bir sonraki oturumda parolayı değiştirmesini gerektiren onay kutusunu seçin.

5. **Oluştur'a** ve ardından Kapat'a **tıklayın.**

     Yeni kullanıcı, Yönetici izinlerine sahip bir grup kullanıcı olan Kullanıcılar grubunda görünür.

## <a name="to-grant-access-to-shared-project-files"></a>Paylaşılan proje dosyalarına erişim izni vermek için

1. Windows Gezgini'nde (Dosya Gezgini), bu kullanıcı tarafından kullanılan ve proje ekibi tarafından paylaşılan proje dosyaları için klasör ağacının kökünü bulun.

     Bu klasörün yolu aşağıdakine benzer olabilir:

    ```cmd
    D:\ourProject
    ```

2. Klasöre sağ tıklayın ve ardından Özellikler'e **tıklayın.**

     Özellikler **\<folder name> iletişim** kutusu görüntülenir.

3. **Güvenlik** sekmesine tıklayın.

4. Grup veya kullanıcı adları kutusunda kullanıcının **hesabının adına** tıklayın.

5. İzinler **kutusunda \<user name>** Tam Denetim onay **kutusunu seçin.**

6. **Tamam**'a tıklayın.

     Bu, kullanıcıya 5. adımda seçilen klasörle başlayan paylaşılan klasör ağacı için izinler sağlar.

## <a name="to-grant-access-to-the-profiling-driver"></a>Profil oluşturma sürücüsüne erişim izni vermek için

1. Yönetici olarak bir komut istemi açın.

2. Dizini şu şekilde değiştirme:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Şu komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Bu komut profil oluşturma araçlarının sürücüsünü yükler ve başlatır.

     Bu komut, yönetici olmayan kullanıcıların Kullanıcı işlem alanı içinde kullanılabilen profil oluşturma özelliklerini kullanamalarını için profil oluşturma sürücüsünü ve hizmetini başlatır. Komutu yalnızca bir Yönetici çalıştırabilirsiniz; ve yönetici olmayan Kullanıcılar için başarısız olur.

     Bu yordamın son adımını da gerçekleştirmedikçe, bilgisayar yeniden başlatıldıktan sonra bu adımın etkilerinin geri alınarak geri alın dikkat edin.

4. Bilgisayara yönetici erişimine sahip bir kullanıcı veya grup tarafından profil oluşturma sürücüsü işlevselliğine erişime izin vermek için komutunu çalıştırın:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Bu komut, veya \<user name> hesabına \<group name> Profil oluşturma araçlarına erişim izni sağlar. \<right>seçeneği, kullanıcının erişebilirsiniz profil oluşturma işlevselliğini belirler. Seçenek \<right> aşağıdaki değerlerden biri veya daha fazlası olabilir:

    - FullAccess : Hizmetlerden performans verileri toplama, örnekleme ve oturumlar arası profil oluşturma dahil olmak üzere tüm profil oluşturma yöntemlerine erişim sağlar.

    - SampleProfiling - örnek profil oluşturma yöntemlerine erişim sağlar

    - Çapraz Geçiş - Profil oluşturma hizmetleri için gerekli olan oturumlar arası profil oluşturma erişimine izin verir.

5. (İsteğe bağlı) Bilgisayar yeniden başlatıldıktan sonra önceki adımlardan herhangi biri sonuçlarını korumak için aşağıdaki komutu çalıştırın:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Belirtilen kullanıcılar oturum açtıktan sonra yönetici izinleri olmadan profil oluşturma araçlarını kullanabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [VSPerfCmd](../profiling/vsperfcmd.md) 
 [Vista Security'Windows profil oluşturma ve oluşturma](../profiling/profiling-and-windows-vista-security.md)
