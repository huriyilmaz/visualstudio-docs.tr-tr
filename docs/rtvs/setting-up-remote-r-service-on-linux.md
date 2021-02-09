---
title: Linux üzerinde uzak R hizmetini ayarlama
description: Ubuntu ve Linux için Windows alt sistemi üzerinde uzak R hizmetini ayarlama.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 586f3038ff4bb091fb99160d7965ad927eda070a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851822"
---
# <a name="remote-r-service-for-linux"></a>Linux için Uzak R Hizmeti

Linux için uzak R hizmeti şu anda rtvs-daemon olarak paketlenmiştir. Arka plan programı Ubuntu 16,04, 16,10 LTS Desktop, Server ve Ubuntu çalıştıran Linux için Windows alt sistemi üzerinde desteklenir ve test edilmiştir. Bu makalenin toplu sayfasında, uzak R hizmetini bu farklı sistemlerde ayarlamaya yönelik yönergeler sağlanmaktadır.

Uzak makineyi yapılandırdıktan sonra, aşağıdaki adımlar Visual Studio için R Araçları (RTVS) bu hizmete bağlanır:

1.   >    >  **Çalışma alanları** penceresini açmak için R araçları Windows **çalışma alanları** ' nı seçin.
1. **Bağlantı ekle**' yi seçin.
1. Bağlama bir ad verin ve URL 'sini sağlayın (örneğin, `https://localhost:5444` Linux için Windows alt sistemi) veya `https://public-ip:5444` (Azure Container). Tamamlandığında **Kaydet** ' i seçin.
1. Bağlantı simgesini seçin veya bağlantı öğesine çift tıklayın.
1. Oturum açma kimlik bilgilerini sağlayın. Kullanıcı adının `<<unix>>\` ' de olduğu gibi `<<unix>>\ruser1` (Linux uzak bilgisayarlara yönelik tüm bağlantılarda olması gerekir) öneki olmalıdır.
1. Otomatik olarak imzalanan sertifika kullanıyorsanız, bir uyarı görebilirsiniz. İleti, uyarıyı düzeltmek için yönergeler sağlar.

## <a name="set-up-remote-r-service"></a>Uzak R hizmetini ayarlama

Bu bölümde aşağıdaki seçenekler açıklanmaktadır:

- [Fiziksel Ubuntu bilgisayarı](#physical-ubuntu-computer)
- [Azure 'da Ubuntu sunucu VM 'si veya Veri Bilimi VM'si](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Yerel veya uzak Docker kapsayıcısı (derlemeyi temizle)](#local-or-remote-docker-container-clean-build)
- [Azure Container Instances üzerinde çalışan kapsayıcı](#container-running-on-azure-container-instances)

Her durumda, uzak bilgisayarda aşağıdaki R yorumlayıcılarını yüklemiş olmanız gerekir:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fiziksel Ubuntu bilgisayarı

1. Bilgisayarda oturum açtıktan sonra rtvs-Daemon tarbol 'yi indirin:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Install betiğini çalıştırın:

    ```bash
    sudo ./rtvs-install
    ```

    Sessiz bir otomasyon için kullanın `sudo ./rtvs-install -s` .

1. Hizmeti etkinleştirme ve başlatma:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. SSL sertifikasını yapılandırın (üretim için gereklidir). Varsayılan olarak, rtvs-Daemon, `ssl-cert-snakeoil.pem` `ssl-cert-snakeoil.pem` paket tarafından oluşturulan ve öğesini kullanır `ssl-cert` . Yükleme sırasında birleştirilirler `ssl-cert-snakeoil.pfx` . Üretim amacıyla, yöneticiniz tarafından sunulan SSL sertifikasını kullanın. SSL sertifikası, içinde bir *. pfx* dosyası ve isteğe bağlı içeri aktarma parolası sağlayarak yapılandırılabilir: */etc/rtvs/rtvsd.config.json*.

1. Seçim Hizmetin çalışıp çalışmadığını denetleyin:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Kullanıcı adı altında çalışan bir işlem görmüyorsanız `rtvssvc` . Aşağıdaki komutu kullanarak başlatın:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Rtvs-Daemon ' ı daha fazla yapılandırmak için bkz `man rtvsd` ..

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Azure 'da Ubuntu sunucu VM 'si veya Veri Bilimi VM'si

#### <a name="create-a-vm"></a>VM oluşturma

1. [Azure portalında](https://portal.azure.com) oturum açın.
1. Sanal makinelere gidin ve **Ekle**' yi seçin.
1. Kullanılabilir VM görüntüleri listesinde aşağıdakilerden birini arayıp seçin:
    - Ubuntu sunucusu: `Ubuntu Server 16.04 LTS`
    - Veri Bilimi VM'si: `Linux Data Science` (Ayrıntılar için bkz. [veri bilimi sanal makineleri](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) )
1. Dağıtım modelini olarak ayarlayın `Resource manager` ve **Oluştur**' u seçin.
1. VM için bir ad seçin, bir Kullanıcı adı ve parola belirtin (SSH ortak anahtar oturumu desteklenmediğinden parola gereklidir).
1. VM yapılandırmasında istediğiniz diğer değişiklikleri yapın.
1. Bir VM boyutu seçin, yapılandırmayı doğrulayın ve **Oluştur**' u seçin. VM oluşturulduktan sonra sonraki bölüme geçin.

#### <a name="configure-the-vm"></a>VM'yi yapılandırma

1. VM 'nin **ağ** bölümünde, izin verilen bir gelen bağlantı noktası olarak 5444 ekleyin. Farklı bir bağlantı noktası kullanmak için RTVS Daemon yapılandırma dosyasında ayarı değiştirin (*/etc/rtvs/rtvsd.config.json*).
1. Seçim Bir DNS adı belirleyin; IP adresini de kullanabilirsiniz.
1. WIndows için PuTTY gibi bir SSH istemcisi kullanarak VM 'ye bağlanın.
1. Yukarıdaki [fiziksel Ubuntu bilgisayarı](#physical-ubuntu-computer) için yönergeleri izleyin.

### <a name="windows-subsystem-for-linux-wsl"></a>Linux için Windows alt sistemi (WSL)

1. [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) veya [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl)için WSL yükleme yönergelerini izleyin.
1. Windows üzerinde Bash 'i başlatın ve bir özel durum içeren bir [fiziksel Ubuntu bilgisayarı](#physical-ubuntu-computer) için önceki yönergeleri izleyin. `rtvsd`WSL Şu anda systemd/systemctl arabirimlerini desteklemediği için, 3. adım yerine komutu kullanarak hizmeti başlatın.

### <a name="local-or-remote-docker-container-clean-build"></a>Yerel veya uzak Docker kapsayıcısı (derlemeyi temizle)

1. Aşağıdaki içeriklerle bir Docker dosyası oluşturun, bu, uzak R hizmeti Daemon 'u ve R 'nin en son sürümünü yüklüyor. **Note**: Bu betik, "foobar" parolasıyla birlikte "ruser1" adlı bir kullanıcı oluşturur ve bu, son iki deyimde istediğiniz gibi değişiklik yapabilir `RUN` .

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

1. Docker dosyasını derleyin ve çalıştırın:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. RTVS 'den kapsar öğesine bağlanmak için `https://localhost:5444` yol, Kullanıcı adı `<<unix>>\ruser1` ve parola kullanın `foobar` . Kapsayıcı uzak bir bilgisayarda çalışıyorsa, `https://remote-host-name:5444` bunun yerine yol olarak kullanın. Bağlantı noktası, *üzerinde/etc/rtvs/rtvsd.config.js* güncelleştirilerek değiştirilebilir.

### <a name="container-running-on-azure-container-instances"></a>Azure Container Instances üzerinde çalışan kapsayıcı

1. Görüntüyü oluşturmak için [yerel veya uzak Docker kapsayıcısında (temiz derleme)](#local-or-remote-docker-container-clean-build) yönergeleri izleyin.
1. Kapsayıcıyı Docker Hub veya Azure Container Repository 'ye gönderin.
1. Azure CLı 'yı başlatın ve komutunu kullanarak oturum açın `az login` .
1. `az container create` `--command-line "rtvsd"` Kapsayıcıyı `rtvsd` bir hizmet olarak çalışacak şekilde ayarladıysanız kullanarak kapsayıcıyı oluşturmak için komutunu kullanın `systemd` . Aşağıdaki komutta, görüntünün Docker Hub 'ında olması beklenmektedir. Azure Container Repository 'yi, kapsayıcı deposu kimlik bilgisi bağımsız değişkenlerini komut satırına ekleyerek de kullanabilirsiniz.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. `az container list`Durumu denetlemek için komutunu kullanın. Ara `provisioningState` : `Succeeded` .
1. Sağlama başarılı olursa artık kapsayıcıya bağlanabilirsiniz. `ipAddress`RTVS 'ten kapsayıcıya bağlanmak için Docker dosyasındaki kimlik bilgileriyle birlikte kullandığınız alanda genel IP adresini arayın.
