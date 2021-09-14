---
title: Azure Tools | kullanarak Bulut Hizmeti yayımlama Microsoft Docs
description: Visual Studio kullanarak Azure bulut hizmeti projelerini yayımlama hakkında Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cd41925fb1b9078b108213870b95d328c81103a0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633057"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Visual Studio kullanarak bulut hizmetini yayımlama

Visual Studio, bir bulut hizmetinin hem Hazırlama hem de Üretim ortamları desteğiyle bir uygulamayı doğrudan Azure'da yayımlar. Yayımlarken dağıtım ortamını ve dağıtım paketi için geçici olarak kullanılan bir depolama hesabını seçersiniz.

Bir Azure uygulaması geliştirme ve test etme aşamasında, web rolleriniz için Web Dağıtımı artımlı olarak yayımlamak üzere Web Dağıtımı'i kullanabilirsiniz. Uygulamanızı bir dağıtım ortamına yayımladıktan sonra Web Dağıtımı doğrudan web rolünü çalıştıran sanal makineye dağıtmanıza olanak sağlar. Değişiklikleri test etmek için web rollerinizi her güncelleştirmek istediğinizde azure uygulamanın tamamını paketleye ve yayımlamaya gerek yok. Bu yaklaşımla, web rolü değişikliklerinizi, uygulamanın bir dağıtım ortamında yayımlanır olması için beklemeden test için bulutta kullanabilirsiniz.

Aşağıdaki yordamları kullanarak Azure uygulamalarınızı yayımlayın ve aşağıdaki adımları kullanarak bir web rolünü Web Dağıtımı:

- Azure uygulamasını Visual Studio'dan yayımlama veya paketle
- Geliştirme ve test döngüsünün bir parçası olarak web rolünü güncelleştirme

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Azure uygulamasını Visual Studio'dan yayımlama veya Visual Studio

Azure uygulamalarınızı yayımlarken aşağıdaki görevlerden birini gerçekleştirebilirsiniz:

- Hizmet paketi oluşturma: Bu paketi ve hizmet yapılandırma dosyasını kullanarak, uygulamanızı bir dağıtım ortamına yayımlamak için [Azure portal.](https://portal.azure.com)

- Azure projenizi Visual Studio: Uygulamayı doğrudan Azure'da yayımlamak için Yayımlama Sihirbazı'nı kullanırsınız. Bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı.](vs-azure-tools-publish-azure-application-wizard.md)

### <a name="to-create-a-service-package-from-visual-studio"></a>Hizmet paketi oluşturmak için Visual Studio

1. Uygulamanızı yayımlamaya hazır olduğunda, Çözüm Gezgini rollerinizi içeren Azure projesinin kısayol menüsünü açın ve Yayımla'yı seçin.

1. Yalnızca bir hizmet paketi oluşturmak için şu adımları izleyin:

   a. Azure projesinin kısayol menüsünde Paket'i **seçin.**

   b. Azure **Uygulamasını Paketle** iletişim kutusunda, paket oluşturmak istediğiniz hizmet yapılandırmasını ve ardından derleme yapılandırmasını seçin.

   c. (İsteğe bağlı) Yayımlandıktan sonra bulut hizmeti için Uzak Masaüstü'leri açmak için Tüm Roller için Uzak **Masaüstünü** Etkinleştir'i ve ardından Uzak Masaüstü **kimlik bilgilerini Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Uzak Masaüstü Bağlantısı kullanarak Azure Cloud Services rolü Visual Studio.](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)

      Yayımladikten sonra bulut hizmetinizin hatasını ayıklamak için Tüm Roller için Uzaktan Hata Ayıklayıcıyı **Etkinleştir'i seçerek uzaktan hata ayıklamayı etkinleştirin.**

   d. Paketi oluşturmak için Paket **bağlantısını** seçin.

      Dosya Gezgini yeni oluşturulan paketin dosya konumunu gösterir. Bu konumu kopyalayıp dosyadan Azure portal.

   e. Bu paketi bir dağıtım ortamında yayımlamak için, bir bulut hizmeti oluşturma ve bu paketi bulut hizmetiyle bir ortama dağıtırken Bu konumu Paket konumu olarak Azure portal.

1. (İsteğe bağlı) Dağıtım işlemini iptal etmek için etkinlik günlüğünde satır öğesinin kısayol menüsünde İptal'i seçin **ve öğesini kaldırın.** Bu komut dağıtım işlemini durdurur ve dağıtım ortamını Azure'dan siler. Dağıtımdan sonra ortamı kaldırmak için aşağıdaki Azure portal.

1. (İsteğe bağlı) Rol örnekleriniz başlatıldıktan sonra, Visual Studio otomatik olarak dağıtım ortamını Cloud Services **düğümde** Sunucu Gezgini. Burada, tek tek rol örneklerinin durumunu görebilir. Bkz. [Cloud Explorer ile Azure kaynaklarını yönetme.](vs-azure-tools-resources-managing-with-cloud-explorer.md) Aşağıdaki çizimde, hala Başlatıyor durumda olan rol örnekleri gösterilmiştir:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Geliştirme ve test döngüsünün bir parçası olarak web rolünü güncelleştirme

Uygulamanın arka uç altyapısı kararlı ancak web rollerinin daha sık güncelleştiriliyor olması gerekirse, Web Dağıtımı kullanarak yalnızca projenizdeki bir web rolünü güncelleştirebilirsiniz. Web Dağıtımı arka uç çalışan rollerini yeniden oluşturmanıza ve yeniden oluşturmanıza gerek yoksa veya birden çok web rolüne sahip olup web rollerinden yalnızca birini güncelleştirmek istediğinizde bu özellik kullanışlıdır.

### <a name="requirements-for-using-web-deploy"></a>Web Dağıtımı kullanma gereksinimleri

- **Yalnızca geliştirme ve test amacıyla:** Değişiklikler doğrudan web rolünün çalıştırıldı olduğu sanal makinede yapılır. Bu sanal makinenin geri dönüştürülmesi gerekirse, yayımlanan özgün paket rolün sanal makinesini yeniden oluşturmak için kullandığı için değişiklikler kaybedilir. Web rolü için en son değişiklikleri almak için uygulamanızı yeniden yayımlar.

- **Yalnızca web rolleri güncelleştirilebilir:** Çalışan rolleri güncelleştirilemez. Ayrıca, içinde 'i `RoleEntryPoint` `web role.cs` güncelleştiresiniz.

- **Bir web rolünün yalnızca tek bir örneğini destekleyene:** Dağıtım ortamınız içinde herhangi bir web rolünün birden çok örneğine sahip olasınız. Ancak, her biri yalnızca bir örneği olan birden çok web rolü de kullanılabilir.

- **Uzak masaüstü bağlantılarını etkinleştirme:** Bu Web Dağıtımı kullanıcı ve parola kullanarak sanal makineye bağlanarak değişiklikleri Internet Information Services (IIS) çalıştıran sunucuya dağıtmanıza olanak sağlar. Ayrıca, bu sanal makinede IIS'ye güvenilen bir sertifika eklemek için sanal makineye bağlanmanız da gerekir. (Bu sertifika, sanal ağ tarafından kullanılan IIS için uzak bağlantının Web Dağıtımı sağlar.)

Aşağıdaki yordam, Azure Uygulamasını Yayımla **sihirbazını kullanmakta olduğunu varsayıyor.**

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Uygulama Web Dağıtımı yayımlarken uygulamayı etkinleştirme

1. Tüm web rolleri **için Web Dağıtımı etkinleştir seçeneğini etkinleştirmek** için önce uzak masaüstü bağlantılarını yapılandırmanız gerekir. Tüm **roller için Uzak Masaüstünü** Etkinleştir'i seçin ve ardından görüntülenen Uzak Masaüstü Yapılandırması kutusunda uzaktan bağlanmak için **kullanılan** kimlik bilgilerini girin. Bkz. [Uzak Masaüstü Bağlantısı kullanarak bir rol Azure Cloud Services için Visual Studio.](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)

1. Uygulamanıza Web Dağıtımı tüm web rolleri için uygulamanıza bir web rolü eklemek için Tüm **web rolleri için Web Dağıtımı'yi seçin.**

    Sarı bir uyarı üçgeni görüntülenir. Web Dağıtımı, varsayılan olarak güvenilmeyen, otomatik olarak imzalanan bir sertifika kullanır ve bu sertifika hassas verileri karşıya yüklemek için önerilmez. Hassas veriler için bu işlemi güvenli hale toplamanız gerekirse, bağlantılara erişim sağlamak için kullanılacak bir SSL Web Dağıtımı ebilirsiniz. Bu sertifikanın güvenilir bir sertifika olması gerekir. Daha fazla bilgi için, [bkz. Make web deploy secure](#make-web-deploy-secure).

1. Özet **ekranı göstermek** için **Sonraki'yi** seçin ve ardından Yayımla'yı seçarak bulut hizmetini dağıtın. 

    Bulut hizmeti yayımlanır. Oluşturulan sanal makinede, web rollerinizi yeniden yayımlamadan güncelleştirmek için Web Dağıtımı için iis için uzak bağlantılar etkinleştirilmiştir.

   > [!NOTE]
   > Bir web rolü için yapılandırılmış birden fazla örneğiniz varsa, her web rolünün yalnızca uygulamanızı yayımlamak için oluşturulan pakette bir örnekle sınırlı olduğunu belirten bir uyarı iletisi görüntülenir. Devam etmek için **Tamam**'ı seçin. Gereksinimler bölümünde belirtildiği gibi, birden fazla web rolünüz olabilir ancak her rolün yalnızca bir örneği olabilir.

### <a name="update-your-web-role-by-using-web-deploy"></a>Web rollerinizi güncelleştirmek için Web Dağıtımı

1. Bu Web Dağıtımı kullanmak için, Visual Studio'de yayımlamak istediğiniz web rollerinden herhangi biri için projede kod değişiklikleri yapın ve ardından çözümünüzdeki bu proje düğümüne sağ tıklayın ve Yayımla'nın üzerine **gelin.** **Web'i Yayımla** iletişim kutusu görüntülenir.

1. (İsteğe bağlı) IIS için uzak bağlantılar için kullanmak üzere bir güvenilen SSL sertifikası eklediyebilirsiniz, Güvenilmeyen **sertifikaya izin** ver onay kutusunun işaretini kaldırın. Güvenliği sağlamak için sertifika ekleme hakkında bilgi Web Dağıtımı, bu makalenin ilerleyen kısımlarında **Web Dağıtımı Güvenli** Hale Web Dağıtımı bölümüne bakın.

1. Bu Web Dağıtımı yayımlama mekanizması, paketi ilk kez yayımlarken Uzak Masaüstü bağlantınız için ayarladığı kullanıcı adı ve parolaya ihtiyaç gösterir.

   a. Kullanıcı **adı alanına** kullanıcı adını girin.

   b. Parola **alanına** parolayı girin.

   c. (İsteğe bağlı) Bu parolayı bu profile kaydetmek için Parolayı **kaydet'i seçin.**

1. Değişiklikleri web rolünüzle yayımlamak için Yayımla'yı **seçin.**

    Durum satırı Yayımlama başlatıldı **olarak görüntülenir.** Yayımlama tamamlandığında Yayımla **başarılı görünür.** Değişiklikler artık sanal makinenizin web rolüne dağıtılmıştır. Artık değişikliklerinizi test etmek için Azure ortamında Azure uygulamanıza başlayabilirsiniz.

### <a name="make-web-deploy-secure"></a>Web dağıtımı güvenliğini sağlama

1. Web Dağıtımı, varsayılan olarak güvenilmeyen, otomatik olarak imzalanan bir sertifika kullanır ve bu sertifika hassas verileri karşıya yüklemek için önerilmez. Hassas veriler için bu işlemi güvenli hale toplamanız gerekirse, bağlantılara erişim sağlamak için kullanılacak bir SSL Web Dağıtımı ebilirsiniz. Bu sertifikanın, bir sertifika yetkilisini (CA) edinen güvenilir bir sertifika olması gerekir.

    Web rol Web Dağıtımı sanal makinelerinizin güvenliğini sağlamak için web dağıtımı için kullanmak istediğiniz güvenilen sertifikayı sanal makineye Azure portal. Bu sertifika, sertifikanın, web rolü için oluşturulan sanal makineye, uygulamanızı yayımlarken eklendiklerine emin olur.

1. Iis'e uzak bağlantılarda kullanmak üzere güvenilen bir SSL sertifikası eklemek için şu adımları izleyin:

   a. Web rolünü çalıştıran sanal makineye bağlanmak **için, Cloud Explorer'da** veya Sunucu Gezgini'da web rolünün örneğini seçin ve ardından Uzak Masaüstü Bağlan seçeneğini **kullanın.** Sanal makineye bağlanma hakkında ayrıntılı adımlar için bkz. Uzak Masaüstü Bağlantısı kullanarak [Azure Cloud Services'da Rol Visual Studio.](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio) Tarayıcınız bir dosyayı indirmenizi `.rdp` istenir.

   b. SSL sertifikası eklemek için IIS Yöneticisi'nde yönetim hizmetini açın. IIS Yöneticisi'nde, Eylem bölmesinde **Bağlamalar bağlantısını açarak** **SSL'yi** etkinleştirin. Site **Bağlaması Ekle** iletişim kutusu görüntülenir. **Ekle'yi** ve ardından Tür **açılan** listesinde HTTPS'yi seçin. SSL **sertifikası listesinde,** bir CA tarafından imzalayan ve sertifika yetkilisine yüklediğiniz SSL sertifikasını Azure portal. Daha fazla bilgi için, [bkz. Configure Connection Ayarlar for the Management Service](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)).

      > [!NOTE]
      > Güvenilen bir SSL sertifikası eklersiniz, yayımla Sihirbazı'nda sarı uyarı **üçgeni artık görünür.**

## <a name="include-files-in-the-service-package"></a>Hizmet paketine dosya dahil etmek

Bir rol için oluşturulan sanal makinede kullanılabilir olacak şekilde hizmet paketinize belirli dosyaları dahil etmek zorundayabilirsiniz. Örneğin, hizmet paketinize başlangıç `.exe` betiği `.msi` tarafından kullanılan bir veya dosyası eklemek istiyor olabilir. Veya bir web rolü veya çalışan rolü projesinin gerektirdiği bir derleme eklemeniz de gerekli olabilir. Dosyaları dahil etmek için Azure uygulamanıza uygun çözüme eklenmeleri gerekir.

1. Bir hizmet paketine derleme eklemek için aşağıdaki adımları kullanın:

   a. Bu **Çözüm Gezgini,** başvurulan derlemenin eksik olduğu projenin proje düğümünü açın.
   b. Derlemeyi projeye eklemek için Başvurular klasörünün kısayol menüsünü açın **ve Başvuru** Ekle'yi **seçin.** Başvuru Ekle iletişim kutusu görüntülenir.
   c. Eklemek istediğiniz başvuruya tıklayın ve ardından Tamam'ı **seçin.** Başvuru, Başvurular klasörünün altındaki **listeye** eklenir.
   d. Ekley istediğiniz derlemenin kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler **penceresi** görüntülenir.

      Bu derlemeyi hizmet paketine dahil etmek için, Yereli **Kopyala listesinde True'yi** **seçin.**
1. Bu **Çözüm Gezgini** başvurulan derlemenin eksik olduğu projenin proje düğümünü açın.

1. Derlemeyi projeye eklemek için Başvurular klasörünün kısayol menüsünü açın **ve Başvuru** Ekle'yi **seçin.** Başvuru **Ekle iletişim** kutusu görüntülenir.

1. Eklemek istediğiniz başvuruya tıklayın ve ardından Tamam **düğmesini** seçin.

    Başvuru, Başvurular klasörünün altındaki **listeye** eklenir.

1. Ekley istediğiniz derlemenin kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler penceresi görüntülenir.

1. Bu derlemeyi hizmet paketine dahil etmek için, Yereli **Kopyala listesinde** True'yi **seçin.**

1. Web rolü projenize eklenmiş olan dosyaları hizmet paketine eklemek için dosyanın kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler **penceresinde Derleme** Eylemi **liste kutusundan** **İçerik'i** seçin.

1. Çalışan rolü projenize eklenmiş olan dosyaları hizmet paketine eklemek için dosyanın kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler penceresinde **Çıkış** dizinine **kopyala liste kutusundan** Daha yeni ise **kopyala'yi** seçin.

## <a name="next-steps"></a>Sonraki adımlar

Azure'da yayımlama hakkında daha fazla bilgi Visual Studio bkz. [Azure Uygulama Yayımlama Sihirbazı.](vs-azure-tools-publish-azure-application-wizard.md)
