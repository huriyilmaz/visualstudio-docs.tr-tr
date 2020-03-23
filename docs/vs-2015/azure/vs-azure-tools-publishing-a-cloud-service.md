---
title: Azure Araçlarını Kullanarak Bulut Hizmeti Yayınlama | Microsoft Dokümanlar
description: Visual Studio'u kullanarak Azure bulut hizmeti projelerini nasıl yayınlayacağınızı öğrenin.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: b959d411f0f574b03729d8016feb6efc531ae171
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302562"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Visual Studio kullanarak bulut hizmetini yayımlama

Visual Studio, bir bulut hizmetinin hem Evreleme hem de Üretim ortamları için destek le birlikte bir uygulamayı doğrudan Azure'da yayımlayabilir. Yayımlarken, dağıtım ortamını ve dağıtım paketi için geçici olarak kullanılan bir depolama hesabı nı seçersiniz.

Bir Azure uygulaması geliştirip sınarken, değişiklikleri web rolleriniz için artımlı olarak yayımlamak için Web Dağıtımı'nı kullanabilirsiniz. Uygulamanızı bir dağıtım ortamında yayımladıktan sonra, Web Dağıtımı değişiklikleri doğrudan web rolünü çalıştıran sanal makineye dağıtmanıza olanak tanır. Değişiklikleri test etmek için web rolünüzü her güncelleştirmek istediğinizde tüm Azure uygulamanızı paketlemeniz ve yayımlamanız gerekmez. Bu yaklaşımla, uygulamanızın dağıtım ortamına yayınlanmasını beklemeden web rol değişikliklerinizin bulutta sınama için kullanılabilir olmasını sağlayabilirsiniz.

Azure uygulamanızı yayımlamak ve Web Dağıtımı'nı kullanarak bir web rolünü güncelleştirmek için aşağıdaki yordamları kullanın:

- Visual Studio'dan Azure uygulaması yayınlama veya paketle
- Geliştirme ve test döngüsünün bir parçası olarak web rolünü güncelleştirme

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Visual Studio'dan bir Azure uygulaması yayımlama veya paketleme

Azure uygulamanızı yayımladığınızda aşağıdaki görevlerden birini yapabilirsiniz:

- Bir hizmet paketi oluşturma: Uygulamanızı [Azure portalından](https://portal.azure.com)bir dağıtım ortamına yayımlamak için bu paketi ve hizmet yapılandırma dosyasını kullanabilirsiniz.

- Azure projenizi Visual Studio'dan yayımlayın: Uygulamanızı doğrudan Azure'da yayımlamak için Yayımlama Sihirbazı'nı kullanırsınız. Bilgi için [bkz.](vs-azure-tools-publish-azure-application-wizard.md)

### <a name="to-create-a-service-package-from-visual-studio"></a>Visual Studio'dan bir hizmet paketi oluşturmak için

1. Uygulamanızı yayımlamaya hazır olduğunuzda, Solution Explorer'ı açın, rollerinizi içeren Azure projesinin kısayol menüsünü açın ve Yayımla'yı seçin.

1. Yalnızca bir hizmet paketi oluşturmak için aşağıdaki adımları izleyin:

   a. Azure projesinin kısayol menüsünde **Paket'i**seçin.

   b. Azure **Uygulaması Paketi** iletişim kutusunda, paket oluşturmak istediğiniz hizmet yapılandırmasını seçin ve ardından yapı yapılandırmasını seçin.

   c. (İsteğe bağlı) Yayımladıktan sonra bulut hizmeti için Uzak Masaüstü'nü açmak **için tüm Roller için Uzak Masaüstü'nü Etkinleştir'i**seçin ve ardından Uzak Masaüstü kimlik bilgilerini yapılandırmak için **Ayarlar'ı** seçin. Daha fazla bilgi için Visual [Studio'u kullanarak Azure Bulut Hizmetlerinde Rol Için Uzak Masaüstü Bağlantısını Etkinleştir'e](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)bakın.

      Bulut hizmetinizi yayımladıktan sonra hata ayıklamak istiyorsanız, tüm Roller için **Uzaktan Hata Ayıklama'yı etkinleştir'i**seçerek uzaktan hata ayıklamayı açın.

   d. Paketi oluşturmak için **Paket** bağlantısını seçin.

      Dosya Gezgini, yeni oluşturulan paketin dosya konumunu gösterir. Azure portalından kullanabilmek için bu konumu kopyalayabilirsiniz.

   e. Bu paketi dağıtım ortamında yayımlamak için, bir bulut hizmeti oluştururken ve bu paketi Azure portalı olan bir ortama dağıtırken bu konumu Paket konumu olarak kullanmanız gerekir.

1. (İsteğe bağlı) Dağıtım işlemini iptal etmek için, etkinlik günlüğündeki satır öğesinin kısayol menüsünde **İptal et ve kaldır'ı**seçin. Bu komut dağıtım işlemini durdurur ve dağıtım ortamını Azure'dan siler. Dağıtımdan sonra ortamı kaldırmak için Azure portalını kullanın.

1. (İsteğe bağlı) Rol örnekleriniz başladıktan sonra Visual Studio, Sunucu Gezgini'ndeki **Bulut Hizmetleri** düğümünde dağıtım ortamını otomatik olarak gösterir. Buradan, tek tek rol örneklerinin durumunu görebilirsiniz. Bkz. [Bulut Gezgini ile Azure kaynaklarını yönetme.](vs-azure-tools-resources-managing-with-cloud-explorer.md) Aşağıdaki resimde, başbaşlatma durumundayken rol örnekleri gösterilmektedir:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Geliştirme ve test döngüsünün bir parçası olarak web rolünü güncelleştirme

Uygulamanızın arka uç altyapısı kararlıysa, ancak web rollerinin daha sık güncelleştirilmesi gerekiyorsa, projenizdeki yalnızca bir web rolünü güncelleştirmek için Web Dağıtımı'nı kullanabilirsiniz. Web Dağıtımı, arka uçtaki çalışan rollerini yeniden oluşturmak ve yeniden dağıtmak istemiyorsanız veya birden çok web roleğiniz varsa ve web rollerinden yalnızca birini güncelleştirmek istediğinizde kullanışlıdır.

### <a name="requirements-for-using-web-deploy"></a>Web Dağıtımı'nı kullanma gereksinimleri

- **Yalnızca geliştirme ve test amacıyla**: Değişiklikler doğrudan web rolünün çalıştığı sanal makineye yapılır. Bu sanal makinenin geri dönüştürülmesi gerekiyorsa, yayımladığın orijinal paket rol için sanal makineyi yeniden oluşturmak için kullanıldığından değişiklikler kaybolur. Web rolü için en son değişiklikleri almak için uygulamanızı yeniden yayımlayın.

- **Yalnızca web rolleri güncellenebilir:** Çalışan rolleri güncelleştirici olamaz. Buna ek olarak, `RoleEntryPoint` in'i `web role.cs`güncelleştiremezsiniz.

- **Yalnızca tek bir web rolü örneğini destekleyebilir:** Dağıtım ortamınızda herhangi bir web rolünün birden çok örneğine sahip olamazsınız. Ancak, her biri yalnızca bir örneği olan birden çok web rolü desteklenir.

- **Uzak masaüstü bağlantılarını etkinleştirme**: Bu gereksinim, Web Dağıtımı'nın internet bilgi hizmetlerini (IIS) çalıştıran sunucuya değişiklikleri dağıtmak için sanal makineye bağlanmak için kullanıcı ve parolayı kullanmasına olanak tanır. Ayrıca, bu sanal makinede IIS'ye güvenilir bir sertifika eklemek için sanal makineye bağlanmanız gerekebilir. (Bu sertifika, Web Deploy tarafından kullanılan IIS için uzak bağlantının güvenli olmasını sağlar.)

Aşağıdaki yordam, **Azure Uygulamasını Yayımla** sihirbazını kullandığınızı varsayar.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Uygulamanızı yayımladığınızda Web Dağıtımı'nı etkinleştirme

1. **Tüm web rolleri için Web Dağıtımını Etkinleştir** seçeneğini etkinleştirmek için öncelikle uzak masaüstü bağlantılarını yapılandırmanız gerekir. Tüm roller için **Uzak Masaüstü'nü Etkinleştir'i** seçin ve ardından görünen **Uzak Masaüstü Yapılandırma** kutusunda uzaktan bağlanmak için kullanılan kimlik bilgilerini sağlayın. [Bkz. Visual Studio'u kullanarak Azure Bulut Hizmetlerinde Rol Için Uzak Masaüstü Bağlantısını Etkinleştir.](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)

1. Uygulamanızdaki tüm web rolleri için Web Dağıtımı'nı etkinleştirmek **için, tüm web rolleri için Web Dağıtımını Etkinleştir'i**seçin.

    Sarı bir uyarı üçgeni görüntülenir. Web Dağıtımı varsayılan olarak güvenilmeyen, kendi imzalı bir sertifika kullanır ve bu sertifika hassas verileri yüklemek için önerilmaz. Bu işlemi hassas veriler için korumanız gerekiyorsa, Web Dağıtım bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın güvenilir bir sertifika olması gerekir. Daha fazla bilgi için [bkz.](#make-web-deploy-secure)

1. **Özet** ekranını göstermek için **İleri'yi** seçin ve bulut hizmetini dağıtmak için **Yayımla'yı** seçin.

    Bulut hizmeti yayımlanır. Oluşturulan sanal makine, Web Dağıtımı'nın web rollerinizi yeniden yayımlamadan güncelleştirmek için kullanılabileceğini, böylece IIS için etkin leştirilmiş uzak bağlantılara sahiptir.

   > [!NOTE]
   > Bir web rolü için yapılandırılan birden fazla örneğiniz varsa, her web rolünün yalnızca uygulamanızı yayımlamak için oluşturulan pakette yalnızca bir örnekle sınırlı olduğunu belirten bir uyarı iletisi görüntülenir. Devam etmek için **Tamam**'ı seçin. Gereksinimler bölümünde belirtildiği gibi, birden fazla web rolüne sahip olabilirsiniz, ancak her rolün yalnızca bir örneği.

### <a name="update-your-web-role-by-using-web-deploy"></a>Web Dağıtımı'nı kullanarak web rolünüzü güncelleştirin

1. Web Dağıtımı'nı kullanmak için Visual Studio'da yayınlamak istediğiniz web rollerinizden herhangi biri için projede kod değişiklikleri yapın ve ardından çözümünüzdeki bu proje düğümünün sağ tıklanması ve **Yayımla'yı**işaret etme noktasına tıklayın. **Web Yayımla** iletişim kutusu görüntülenir.

1. (İsteğe bağlı) IIS için uzak bağlantılar için kullanmak üzere güvenilir bir SSL sertifikası eklediyseniz, **güvenilmeyen sertifika** onay kutusunu temizleyebilirsiniz. Web Dağıtımı'nı güvenli hale getirmek için sertifika ekleme hakkında bilgi için, bu makalenin ilerleyen bölümlerinde **Web Dağıtımını Güvenli Hale Getirme** bölümüne bakın.

1. Web Dağıtımı'nı kullanmak için yayımlama mekanizmasının, paketi ilk yayımladığınızda Uzak Masaüstü bağlantınız için ayarladığınız kullanıcı adı ve parolaya ihtiyacı vardır.

   a. **Kullanıcı adına,** kullanıcı adını girin.

   b. **Parola'da,** parolayı girin.

   c. (İsteğe bağlı) Bu parolayı bu profile kaydetmek istiyorsanız, **parolayı kaydet'i**seçin.

1. Web rolünüzdeyapılan değişiklikleri yayımlamak için **Yayımla'yı**seçin.

    Durum satırı **yayımla'yı görüntüler.** Yayımlama tamamlandığında, **Yayımla** başarılı görünür. Değişiklikler artık sanal makinenizdeki web rolüne dağıtıldı. Artık değişikliklerinizi test etmek için Azure uygulamanızı Azure ortamında başlatabilirsiniz.

### <a name="make-web-deploy-secure"></a>Web dağıtımGüvenliğini güvenli hale getirin

1. Web Dağıtımı varsayılan olarak güvenilmeyen, kendi imzalı bir sertifika kullanır ve bu sertifika hassas verileri yüklemek için önerilmaz. Bu işlemi hassas veriler için korumanız gerekiyorsa, Web Dağıtım bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın, sertifika yetkilisinden (CA) aldığınız güvenilir bir sertifika olması gerekir.

    Web Dağıtımı'nı her web rolünüzün her sanal makinesi için güvenli hale getirmek için, web dağıtımı için kullanmak istediğiniz güvenilir sertifikayı Azure portalına yüklemeniz gerekir. Bu sertifika, uygulamanızı yayımladığınızda web rolü için oluşturulan sanal makineye sertifikanın eklenmesini sağlar.

1. Uzak bağlantılar için kullanmak üzere IIS'ye güvenilir bir SSL sertifikası eklemek için aşağıdaki adımları izleyin:

   a. Web rolünü çalıştıran sanal makineye bağlanmak için **Bulut Gezgini** veya Sunucu **Gezgini'ndeki**web rolü örneğini seçin ve ardından Uzak Masaüstü komutunu **kullanarak Bağlan'ı** seçin. Sanal makineye nasıl bağlanışgösteriz hakkında ayrıntılı adımlar için Visual [Studio'yu kullanarak Azure Bulut Hizmetlerinde Rol Için Uzak Masaüstü Bağlantısını Etkinleştir'e](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)bakın. Tarayıcınız bir `.rdp` dosyayı indirmenizi ister.

   b. SSL sertifikası eklemek için Yönetim hizmetini IIS Manager'da açın. IIS Manager'da, **Eylem** bölmesinde **Bağlayıcılar** bağlantısını açarak SSL'yi etkinleştirin. **Site Bağlama Ekle** iletişim kutusu görüntülenir. **Ekle'yi**seçin ve ardından **Açılan Yazı** listesinde HTTPS'yi seçin. **SSL sertifika** listesinde, BIR CA tarafından imzaladığınız ve Azure portalına yüklediğiniz SSL sertifikasını seçin. Daha fazla bilgi için, [Yönetim Hizmeti için Bağlantı Ayarlarını Yapılandır'a](https://technet.microsoft.com/library/cc770458(WS.10).aspx)bakın.

      > [!NOTE]
      > Güvenilir bir SSL sertifikası eklerseniz, **yayımlama sihirbazında**sarı uyarı üçgeni artık görünmez.

## <a name="include-files-in-the-service-package"></a>Servis paketine dosyaları ekleme

Bir rol için oluşturulan sanal makinede kullanılabilmeleri için hizmet paketinize belirli dosyaları eklemeniz gerekebilir. Örneğin, hizmet paketinize başlangıç `.exe` komut `.msi` dosyası tarafından kullanılan bir dosya veya dosya eklemek isteyebilirsiniz. Veya bir web rolü veya işçi rol projesi gerektiren bir derleme eklemeniz gerekebilir. Dosyaları eklemek için Azure uygulamanız için çözüme eklenmesi gerekir.

1. Bir hizmet paketine derleme eklemek için aşağıdaki adımları kullanın:

   a. **Çözüm Gezgini'nde,** başvurulan derlemeeksik proje için proje düğümlerini açın.
   b. Derlemeyi projeye eklemek **için, Başvurular** klasörünün kısayol menüsünü açın ve ardından **Başvuru Ekle'yi**seçin. Başvuru Ekle iletişim kutusu görüntülenir.
   c. Eklemek istediğiniz başvuruyu seçin ve ardından **Tamam'ı**seçin. Başvuru, **Başvurular** klasörü altındaki listeye eklenir.
   d. Eklediğiniz derleme için kısayol menüsünü açın ve **Özellikler'i**seçin. **Özellikler** penceresi görüntülenir.

      Bu derlemeyi hizmet paketine eklemek için **Yerel Kopyala listesine** **True'yu**seçin.
1. **Çözüm Gezgini'nde** başvurulan derleme eksik proje için proje düğümü açın.

1. Derlemeyi projeye eklemek **için, Başvurular** klasörünün kısayol menüsünü açın ve ardından **Başvuru Ekle'yi**seçin. **Başvuru Ekle** iletişim kutusu görüntülenir.

1. Eklemek istediğiniz başvuruyu seçin ve ardından **Tamam** düğmesini seçin.

    Başvuru, **Başvurular** klasörü altındaki listeye eklenir.

1. Eklediğiniz derleme için kısayol menüsünü açın ve **Özellikler'i**seçin. Özellikler penceresi görüntülenir.

1. Bu derlemeyi hizmet paketine eklemek için **Yerel Kopyala** listesine **True'yu**seçin.

1. Web rol projenize eklenen servis paketine dosyaları eklemek için, dosyanın kısayol menüsünü açın ve ardından **Özellikler'i**seçin. **Özellikler** penceresinden **Eylem Oluştur** liste kutusundan **İçerik'i** seçin.

1. İşçi rol projenize eklenen dosyaları hizmet paketine eklemek için dosyanın kısayol menüsünü açın ve ardından **Özellikler'i**seçin. **Özellikler** penceresinden, Kopya'dan çıktı **dizini** listesi kutusuna **yeniyse Kopyala'yı** seçin.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'dan Azure'da yayımlama hakkında daha fazla bilgi edinmek için [bkz.](vs-azure-tools-publish-azure-application-wizard.md)
