---
title: 'Nasıl yapılır: Izinleri ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03991f3d5900377ceca5464bf41cfb90fcae650e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64838047"
---
# <a name="how-to-set-permissions"></a>Nasıl Yapılır: İzinleri Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, bir bilgisayarın yöneticisinin, bu bilgisayarda yönetici izinlerine sahip olmayan bir kullanıcı veya gruba profil oluşturma için gerekli güvenlik izinlerini nasıl verdiğini açıklar.  
  
 Temel güvenlik prensibi, uygulamaların ihtiyaç duydukları izinlerle daha fazla olmadan çalışması gerektiğini belirtir. Bu ilke, kullanıcılar için de geçerlidir. Kullanıcılar, Yöneticiler grubu yerine kullanıcılar grubunun üyeleri olarak oturum açtıklarında tamamen etkili olabilecekleri takdirde, yönetici izinleri verilmemelidir. İlk yordam olan "Kullanıcı izinleri olan bir kullanıcı hesabı oluşturmak Için", kullanıcılar grubunun bir üyesi için bir kullanıcı hesabının nasıl oluşturulacağını açıklar.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Kullanıcılar grubunun üyeleri, ekibin diğer üyeleriyle paylaşılan disk üzerindeki klasörlere ve dosyalara erişmesi gerekir. "Paylaşılan proje dosyalarına erişim izni vermek Için" ikinci yordam, bu erişimin nasıl verildiğini açıklar.  
  
  Yönetici, profil oluşturma araçlarının yazılım sürücüsüne erişim izni veriyorsa, kullanıcılar grubunun üyeleri profil oluşturma araçlarını çalıştırabilir. Son yordam olan "profil oluşturma sürücüsüne erişim izni vermek Için", bu sürücüye erişim verme işlemini açıklar.  
  
> [!NOTE]
> Bu yordamlardaki adımları izlemek için yönetici izinlerine sahip olmanız gerekir.  
  
### <a name="to-create-a-user-account-that-has-user-permissions"></a>Kullanıcı izinlerine sahip bir kullanıcı hesabı oluşturmak için  
  
1. Bilgisayarım ' a sağ **tıklayın ve ardından** **Yönet**' e tıklayın.  
  
     **Bilgisayar Yönetimi** penceresi açılır.  
  
2. **Yerel kullanıcılar ve gruplar '** ı genişletin.  
  
3. **Kullanıcılar** klasörüne sağ tıklayın ve ardından **Yeni Kullanıcı**' ya tıklayın.  
  
     **Yeni Kullanıcı** iletişim kutusu görüntülenir.  
  
4. Bu iletişim kutusundaki alanları oluşturmakta olduğunuz Kullanıcı hesabının bilgileriyle doldurun. Bir parola belirtin. İsteğe bağlı olarak, kullanıcının bir sonraki oturum açışında parolayı değiştirmesini gerektiren onay kutusunu seçin.  
  
5. **Oluştur** ' a tıklayın ve ardından **Kapat**' a tıklayın.  
  
     Yeni Kullanıcı, yönetici izinlerine sahip olmayan bir Kullanıcı grubu olan kullanıcılar grubunda görüntülenir.  
  
### <a name="to-grant-access-to-shared-project-files"></a>Paylaşılan proje dosyalarına erişim izni vermek için  
  
1. Windows Gezgini 'nde (veya dosya Gezgini), bu kullanıcı tarafından kullanılan ve proje ekibi tarafından paylaşılan proje dosyaları için klasör ağacının kökünü bulun.  
  
     Bu klasörün yolu aşağıdakine benzeyebilir:  
  
    ```  
    D:\ourProject  
    ```  
  
2. Klasöre sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
     ** \<folder name> Özellikler** iletişim kutusu görüntülenir.  
  
3. **Güvenlik** sekmesine tıklayın.  
  
4. **Grup veya Kullanıcı adları** kutusunda Kullanıcı hesabının adına tıklayın.  
  
5. ** \<user name> İzinler** kutusunda, **tam denetim**onay kutusunu seçin.  
  
6. **Tamam**’a tıklayın.  
  
     Bu, kullanıcıya, 5. adımda seçilen klasörle başlayan paylaşılan klasör ağacı için izin verir.  
  
### <a name="to-grant-access-to-the-profiling-driver"></a>Profil oluşturma sürücüsüne erişim izni vermek için  
  
1. Yönetici olarak bir komut istemi açın.  
  
2. Dizini şu şekilde değiştirin:  
  
   ```  
   <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
   ```  
  
3. Şu komutu çalıştırın:  
  
   ```  
   vsperfcmd /admin:driver,start /admin:service,start  
   ```  
  
    Bu komut, profil oluşturma araçları için sürücüyü yükleyip başlatır.  
  
    Bu komut, yönetici olmayan kullanıcıların kullanıcı işlem alanında kullanılabilen profil oluşturma özelliklerini kullanabilmesi için profil oluşturma sürücüsünü ve hizmetini başlatır. Yalnızca bir yönetici komutu çalıştırabilir; Yönetici olmayan kullanıcılar için başarısız olur.  
  
    Bu yordamın son adımını da gerçekleştirmediğiniz müddetçe, bu adımın etkilerinin bilgisayar yeniden başlatıldıktan sonra geri alındığına dikkat edin.  
  
4. Bilgisayara yönetici erişimi olmayan bir kullanıcı veya grup tarafından profil oluşturma sürücüsü işlevine erişime izin vermek için komutunu çalıştırın:  
  
   ```  
   vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
   ```  
  
    Bu komut, \<user name> veya \<group name> hesabına profil oluşturma araçlarına erişim izni verir. \<right>Seçeneği, kullanıcının erişebileceği profil oluşturma işlevini belirler. \<right>Bu seçenek, aşağıdaki değerlerden biri veya daha fazlası olabilir:  
  
   - FullAccess-hizmetler, örnekleme ve çapraz oturum profillendirme dahil olmak üzere tüm profil oluşturma yöntemlerine erişim sağlar.  
  
   - Sampleprofil oluşturma-örnek profil oluşturma yöntemlerine erişime izin verir  
  
   - CrossSession-profil oluşturma hizmetleri için gerekli olan çapraz oturum profili oluşturma erişimine izin verir.  
  
5. Seçim Bilgisayar yeniden başlatıldıktan sonra önceki adımlardan herhangi birinin sonuçlarını korumak için aşağıdaki komutu çalıştırın:  
  
   ```  
   vsperfcmd /admin:driver,autostart,on  
   ```  
  
   Belirtilen kullanıcılar, oturum açtıktan sonra, artık profil oluşturma araçlarını yönetici izinleri olmadan kullanabiliyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)
