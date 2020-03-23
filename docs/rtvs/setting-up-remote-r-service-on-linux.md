---
title: Linux'ta Uzaktan R Hizmeti Kurma
description: Ubuntu'da Uzaktan R Hizmeti ve Linux için Windows Alt Sistemi nasıl kurulamaz?
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809563"
---
# <a name="remote-r-service-for-linux"></a>Linux için Uzak R Hizmeti

Linux için Uzaktan R Hizmeti şu anda rtvs-daemon olarak paketlenmiştir. Daemon Ubuntu 16.04, 16.10 LTS masaüstü, sunucu ve Linux çalışan Ubuntu için Windows Alt sistemi üzerinde desteklenir ve test edilmiştir. Bu makalenin büyük bölümü, bu farklı sistemlerde Uzaktan R Hizmeti kurmak için yönergeler sağlar.

Uzak makineyi yapılandırdıktan sonra, aşağıdaki adımlar Visual Studio için R Tools (RTVS) ile bu hizmete bağlanır:

1. Çalışma Alanları penceresini açmak için **R Tools** > **Windows** > Çalışma**Alanlarını'nı** seçin. **Workspaces**
1. **Bağlantı Ekle'yi**seçin.
1. Bağlanağa bir ad verin ve (Linux için Windows Alt `https://public-ip:5444` Sistemi) veya (Azure kapsayıcısı) gibi `https://localhost:5444` URL'sini sağlayın. Tamamlandığında **Kaydet'i** seçin.
1. Bağlantı simgesini seçin veya bağlantı öğesini çift tıklatın.
1. Oturum açma kimlik bilgilerini sağlayın. Kullanıcı adı (Linux uzak `<<unix>>\` bilgisayarlara tüm bağlantılar için gerekli) gibi `<<unix>>\ruser1` önceden belirlenmiş olmalıdır.
1. Kendi imzalı sertifika kullanıyorsanız, bir uyarı görebilirsiniz. İleti, uyarıyı düzeltmek için yönergeler sağlar.

## <a name="set-up-remote-r-service"></a>Uzaktan R Hizmetini Ayarlama

Bu bölümde aşağıdaki seçenekler açıklanmaktadır:

- [Fiziksel Ubuntu bilgisayar](#physical-ubuntu-computer)
- [Azure'da Ubuntu Server VM veya Data Science VM](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Yerel veya uzak Docker konteyneri (temiz yapı)](#local-or-remote-docker-container-clean-build)
- [Azure Kapsayıcı Örneklerinde Çalışan Kapsayıcı](#container-running-on-azure-container-instances)

Her durumda, uzak bilgisayarda aşağıdaki R yorumlayıcılarından biri yüklü olmalıdır:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fiziksel Ubuntu bilgisayar

1. Bir kez bilgisayara giriş, rtvs-daemon tarball indirin:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Yükleme komut dosyasını çalıştırın:

    ```bash
    sudo ./rtvs-install
    ```

    Sessiz bir otomasyon `sudo ./rtvs-install -s`için.

1. Hizmeti etkinleştirin ve başlatın:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. SSL sertifikasını yapılandırın (üretim için gereklidir). Varsayılan olarak, rtvs-daemon `ssl-cert-snakeoil.pem` `ssl-cert-snakeoil.pem` kullanır ve `ssl-cert` paket tarafından oluşturulan. Kurulum sırasında, onlar içine `ssl-cert-snakeoil.pfx`birleştirilir. Üretim amacıyla yöneticiniz tarafından sağlanan SSL sertifikasını kullanın. SSL sertifikası *bir .pfx* dosya ve isteğe bağlı alma şifresi sağlayarak yapılandırılabilir: */etc/rtvs/rtvsd.config.json*.

1. (İsteğe bağlı) Hizmetin çalışır durumda olup olmadığını denetleyin:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Kullanıcı adı `rtvssvc`altında çalışan bir işlem görmüyorsanız. Aşağıdaki komutu kullanarak başlatın:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Rtvs-daemon daha fazla yapılandırmak `man rtvsd`için bkz.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Azure'da Ubuntu Server VM veya Data Science VM

#### <a name="create-a-vm"></a>VM oluşturma

1. [Azure portalında](https://portal.azure.com)oturum açın.
1. Sanal Makinelere gidin ve ardından **Ekle'yi**seçin.
1. Kullanılabilir VM görüntüleri listesinde aşağıdakilerden birini arayın ve seçin:
    - Ubuntu Sunucu:`Ubuntu Server 16.04 LTS`
    - Veri Bilimi VM: `Linux Data Science` (ayrıntılar için Data Science Sanal [Makineler](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) e bakınız)
1. Dağıtım modelini `Resource manager` oluştur'a ayarlayın ve **seçin.**
1. VM için bir ad seçin, bir kullanıcı adı ve parola sağlayın (SSH ortak anahtar girişi desteklenmedığından parola gereklidir).
1. VM yapılandırması için istenen diğer değişiklikleri yapın.
1. Bir VM boyutu seçin, yapılandırmayı doğrulayın ve **Oluştur'u**seçin. VM oluşturulduktan sonra bir sonraki bölüme geçin.

#### <a name="configure-the-vm"></a>VM yapılandırma

1. VM'nin **Ağ bölümüne,** izin verilen gelen bağlantı noktası olarak 5444 ekleyin. Farklı bir bağlantı noktası kullanmak için, RTVS daemon config dosyasındaki ayarı değiştirin (*/etc/rtvs/rtvsd.config.json*).
1. (İsteğe bağlı) Bir DNS adı ayarlayın; IP adresini de kullanabilirsiniz.
1. WIndows için PuTTY gibi bir SSH istemcisi kullanarak VM'ye bağlanın.
1. Yukarıdaki [Fiziksel Ubuntu bilgisayar](#physical-ubuntu-computer) için yönergeleri izleyin.

### <a name="windows-subsystem-for-linux-wsl"></a>Linux için Windows Alt Sistemi (WSL)

1. [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) veya [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl)için WSL yükleme yönergelerini izleyin.
1. Windows'da bash başlatın ve bir istisna dışında bir [Fiziksel Ubuntu bilgisayar](#physical-ubuntu-computer) önceki yönergeleri izleyin. Adım 3 için, WSL `rtvsd`şu anda systemd/systemctl arabirimlerini desteklemediği için hizmeti komutu kullanarak başlatın.

### <a name="local-or-remote-docker-container-clean-build"></a>Yerel veya uzak Docker konteyneri (temiz yapı)

1. Aşağıdaki içeriği içeren ve Uzak R hizmeti daemon'unu ve R. **Note'un**en son sürümünü yükleyen bir Docker dosyası oluşturun: Bu komut dosyası, son iki `RUN` ifadede istediğiniz gibi değiştirebileceğiniz "foobar" parolasıyla "ruser1" adlı bir kullanıcı oluşturur.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Docker dosyasını oluşturun ve çalıştırın:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. RTVS'den içerdiğine bağlanmak `https://localhost:5444` için yol, kullanıcı `<<unix>>\ruser1`adı `foobar`ve parola olarak kullanın. Kapsayıcı uzak bir bilgisayarda çalışıyorsa, bunun yerine yol olarak kullanın. `https://remote-host-name:5444` Bağlantı noktası güncellenerek değiştirilebilir */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Azure Kapsayıcı Örneklerinde Çalışan Kapsayıcı

1. Görüntüyü oluşturmak için [Yerel veya uzak Docker kapsayıcısındaki (temiz yapı)](#local-or-remote-docker-container-clean-build) yönergeleri izleyin.
1. Kapsayıcıyı Docker hub'ına veya Azure Kapsayıcı Deposu'na itin.
1. Azure CLI'yi başlatın `az login` ve komutu kullanarak oturum açın.
1. Kapsayıcıyı `az container create` `systemd` hizmet olarak çalışacak `rtvsd` `--command-line "rtvsd"` şekilde ayarlamadıysanız, kapsayıcıyı kullanmak için komutu kullanın. Aşağıdaki komutta, görüntünün Docker hub'ında olması beklenmektedir. Komut satırına Kapsayıcı Deposu kimlik bağımsız değişkenlerini ekleyerek Azure Kapsayıcı Deposu'nu da kullanabilirsiniz.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Durumu `az container list` denetlemek için komutu kullanın. Bak `provisioningState`: `Succeeded`.
1. Sağlama başarılı olduysa, artık kapsayıcıya bağlanabilirsiniz. RTVS'den kapsayıcıya `ipAddress` bağlanmak için docker dosyasındaki kimlik bilgileriyle birlikte kullandığınız alanda genel IP adresine bakın.
