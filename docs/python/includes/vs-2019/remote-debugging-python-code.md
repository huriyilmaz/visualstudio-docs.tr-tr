---
title: Uzak Linux bilgisayarlarda Python kodunda hata ayıklama
description: Gerekli Visual Studio, güvenlik ve sorun giderme dahil olmak üzere uzak Linux bilgisayarlarda çalışan Python kodunda hata ayıklamak için Visual Studio kullanın.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 74b4e25bccf52893302adf4bca6bb81a5e7e3794
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140543"
---
Visual Studio bir bilgisayarda Python uygulamalarını yerel olarak ve uzaktan başlatabiliyor ve hata Windows [(bkz. Uzaktan hata ayıklama).](../../../debugger/remote-debugging.md) Ayrıca, hata ayıklama kitaplığını kullanarak CPython dışında farklı bir işletim sisteminde, cihazda veya Python uygulamasında [uzaktan hata ayıklar.](https://pypi.org/project/debugpy/)

Hata ayıklama kullanılırken, hata ayıklama yapılan Python kodu, hata ayıklama sunucusunun Visual Studio barındırabilir. Bu barındırma, kodunuzun sunucuyu içeri aktarması ve etkinleştirmesi için küçük bir değişiklik gerektirir ve TCP bağlantılarına izin vermek için uzak bilgisayarda ağ veya güvenlik duvarı yapılandırmaları gerekebilir.

> [!NOTE]
> 2019 Visual Studio 16.4 ve önceki sürümlerde [ptvsd kitaplığı](https://pypi.python.org/pypi/ptvsd) kullanılmıştır. Hata ayıklama kitaplığı, Visual Studio 2019 sürüm 16.5'te ptvsd 4'ü değiştirmıştı.

## <a name="set-up-a-linux-computer"></a>Linux bilgisayar ayarlama

Bu izlenecek yolu takip etmek için aşağıdaki öğeler gereklidir:

- Mac OSX veya Linux gibi bir işletim sisteminde Python çalıştıran uzak bir bilgisayar.
- 5678 (gelen) bağlantı noktası, uzaktan hata ayıklama için varsayılan seçenek olan bilgisayarın güvenlik duvarında açılır.

> [!NOTE]
> Bu kılavuz, 2019 Visual Studio 16.6'ya dayalıdır.

Azure'da kolayca [bir Linux sanal makinesi oluşturabilir ve sanal](/azure/virtual-machines/linux/creation-choices) [makineden Uzak Masaüstü'Windows.](/azure/virtual-machines/linux/use-remote-desktop) Python varsayılan olarak yüklü olduğundan VM için Ubuntu kullanışlıdır; aksi takdirde, ek [Python indirme konumları için tercih istediğiniz Python yorumlayıcıyı](../../installing-python-interpreters.md) yükleme listesine bakın.

Azure VM'leri için güvenlik duvarı kuralı oluşturma hakkında ayrıntılı bilgi için bkz. Azure'da bağlantı noktalarını [Azure portal.](/azure/virtual-machines/windows/nsg-quickstart-portal)

## <a name="prepare-the-script-for-debugging"></a>Betiği hata ayıklama için hazırlama

1. Uzak bilgisayarda, aşağıdaki kodla guessing-game.py *adlı* bir Python dosyası oluşturun:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. kullanarak `debugpy` paketi ortamınıza `pip3 install debugpy` yükleyin.
   >[!NOTE]
   >Sorun giderme için ihtiyacınız olması durumunda yüklü olan hata ayıklama sürümünü kaydetmek iyi bir fikirdir; hata [ayıklama listesi kullanılabilir](https://pypi.org/project/debugpy/) sürümleri de gösterir.

1. Uzaktan hata ayıklamayı etkinleştirmek için aşağıdaki kodu diğer kodun guessing-game.py en erken noktasından önce girin. (Katı bir gereksinim değildir ancak işlev çağrılmadan önce ortaya çıkacak arka plan iş parçacıklarında `listen` hata ayıklamak mümkün değildir.)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Dosyayı kaydedin ve `python3 guessing-game.py` çalıştırın. çağrısı arka `listen` planda çalışır ve siz programla etkileşim kurduğunda gelen bağlantıları bekler. İsterseniz, hata `wait_for_client` ayıklayıcı eklenene `listen` kadar programı engellemek için işlevi sonra çağrılabiliyor.

> [!Tip]
> ve 'ye ek olarak, hata ayıklayıcısı ekli ise programlı kesme noktası işlevi sunan bir yardımcı `listen` `wait_for_client` işlevi de `breakpoint` sağlar. Hata ayıklayıcı ekli ise döndüren bir işlev de vardır (diğer işlevleri çağırmadan önce bu sonucu `is_client_connected` `True` denetlemeye gerek olmadığını `debugpy` unutmayın).

## <a name="attach-remotely-from-python-tools"></a>Python Araçları'dan uzaktan ekleme

Bu adımlarda, uzak işlemi durdurmak için basit bir kesme noktası ayarlayacağız.

1. Yerel bilgisayarda uzak dosyanın bir kopyasını oluşturun ve yerel bilgisayarda Visual Studio. Dosyanın nerede bulunduğu önemli değildir, ancak adı uzak bilgisayarda betiğin adıyla eşleşmesi gerekir.

1. (İsteğe bağlı) Yerel bilgisayarınızda hata ayıklama için IntelliSense'in olması için python ortamınıza hata ayıklama paketini yükleyin.

1. İşleme **Eklemede**  >  **Hata Ayıkla'ya seçin.**

1. Görüntülenen İşleme **Ekle iletişim kutusunda** Bağlantı Türü'lerini Python **uzak** **(hata ayıklama) olarak ayarlayın.**

1. Bağlantı **Hedefi alanına** uzak bilgisayarın (açık bir adres veya myvm.cloudapp.net gibi bir ad olabilir) nerede olduğunu ve uzaktan hata ayıklama bağlantı noktası `tcp://<ip_address>:5678` numarası olduğunu `<ip_address>` `:5678` girin.

1. Bu bilgisayarda kullanılabilir hata ayıklama işlemlerinin listesini doldurmak için **Enter** tuşuna basın:

    ![Bağlantı hedefi ve listeleme işlemlerini girme](../../media/remote-debugging-attach.png)

    Bu listeyi girdikten sonra uzak bilgisayarda başka bir program başlatıyorsanız Yenile **düğmesini** seçin.

1. Hata ayıklama işlemini seçin ve ardından **Ekle'yi** seçin veya işleme çift tıklayın.

1. Visual Studio, betik uzak bilgisayarda çalışırken hata ayıklama moduna geçer ve her zamanki hata ayıklama [özelliklerini](../../debugging-python-in-visual-studio.md) sağlar. Örneğin, satırda bir kesme noktası `if guess < number:` ayarlayın, sonra uzak bilgisayara geçiş ve başka bir tahmin girin. Bunu tamamladikten sonra Visual Studio kesme noktalarında durur, yerel değişkenleri gösterir ve bu şekilde devam eder:

    ![Visual Studio noktası isabet olduğunda hata ayıklamayı duraklatıyor](../../media/remote-debugging-breakpoint-hit.png)

1. Hata ayıklamayı durdur Visual Studio uzak bilgisayarda çalıştırmaya devam eden programdan ayrılır. hata ayıklama ayrıca hata ayıklayıcıları eklemeyi dinlemeye devam eder, böylece işleme herhangi bir zamanda yeniden iliştirilmenizi sağlar.

### <a name="connection-troubleshooting"></a>Bağlantı sorunlarını giderme

1. Bağlantı Türü olarak Python uzak **(hata ayıklama) seçtiğinizden** **emin olun**
1. Bağlantı Hedefi'nde yer alan gizli **kodun uzak** kodda yer alan gizli ile tam olarak eş olup olamay olduğunu kontrol edin.
1. Bağlantı Hedefi'nde IP **adresinin uzak** bilgisayarın ip adresiyle eşle eş olup olamay olduğunu kontrol edin.
1. Uzak bilgisayarda uzaktan hata ayıklama bağlantı noktasını açtığınızı ve bağlantı hedefine gibi bağlantı noktası soneki ekini dahil edin. `:5678`
    - Farklı bir bağlantı noktası kullanmak gerekirse, içinde olduğu gibi `listen` içinde `debugpy.listen((host, port))` belirtabilirsiniz. Bu durumda, güvenlik duvarında ilgili bağlantı noktasını açın.
1. Aşağıdaki tabloda, uzak bilgisayarda yüklü olan hata ayıklama sürümünün, Visual Studio'de kullanmakta olan Python araçlarının sürümü tarafından kullanılan `pip3 list` eşleşmeler tarafından döndürülerek Visual Studio kontrol edin. Gerekirse, uzak bilgisayarda hata ayıklamayı güncelleştirin.

    | Visual Studio sürüm | Python araçları/hata ayıklama sürümü |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> Visual Studio 2019 sürüm 16.0-16.4 hata ayıklama değil ptvsd kullanıldı. Bu sürümler için bu kılavuzda yer alan süreç benzerdir, ancak işlev adları farklıdır. Visual Studio 2019 sürüm 16.5 hata ayıklama kullanır, ancak işlev adları ptvsd'de bulunan adlar ile aynıdır. yerine `listen` `enable_attach` kullanabilirsiniz. yerine `wait_for_client` `wait_for_attach` kullanabilirsiniz. yerine `breakpoint` `break_into_debugger` kullanabilirsiniz.

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Eski hata ayıklama için ptvsd 3.x kullanma
Visual Studio 2017 sürüm 15.8 ve sonrası ptvsd sürüm 4.1+ tabanlı bir hata ayıklayıcı kullanır. Visual Studio 2019 sürüm 16.5 ve sonrası, hata ayıklamayı temel alan bir hata ayıklayıcı kullanır. Hata ayıklayıcının bu sürümleri Python 2.7 ve Python 3.5+ ile uyumludur. Python 2.6, 3.1 ile 3.4 veya IronPython kullanıyorsanız Visual Studio hata gösterir, Hata Ayıklayıcı bu **Python ortamını desteklemez.** Aşağıdaki bilgiler yalnızca ptvsd 3.x ile uzaktan hata ayıklama için geçerlidir.

1. ptvsd 3.x ile işlev, çalışan betikle erişimi kısıtlayan ilk bağımsız değişken olarak bir "gizli" değeri `enable_attach` geçmeni gerekli kıldı. Uzaktan hata ayıklayıcıyı iliştirme sırasında bu gizli kodu girersiniz. Önerilmez, ancak herkesin bağlanmasına izin ve ardından `enable_attach(secret=None)` kullanın.

1. Bağlantı hedefi `tcp://<secret>@<ip_address>:5678` URL'si burada `<secret>` Python kodunda geçirilen `enable_attach` dizedir.

Varsayılan olarak, ptvsd 3.x uzaktan hata ayıklama sunucusuna bağlantı yalnızca gizli ile güvenli hale getirildi ve tüm veriler düz metin olarak geçirildi. Daha güvenli bir bağlantı için ptvsd 3.x, aşağıdaki gibi ayar varsayılan `tcsp` protokolünü kullanarak SSL'yi destekler:

1. Uzak bilgisayarda, openssl kullanarak ayrı otomatik olarak imzalanan sertifika ve anahtar dosyaları oluştur:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    İstendiğinde, openssl tarafından istendiğinde Ortak Ad için  ana bilgisayar adını veya IP adresini (bağlanmak için kullanırsanız) kullanın.

    (Ek ayrıntılar için Python [modülü belgelerde](https://docs.python.org/3/library/ssl.html#self-signed-certificates) `ssl` otomatik olarak imzalanan sertifikalar'a bakın. Bu belgelerde komutun yalnızca tek bir birleşik dosya oluşturacağına dikkat olun.)

1. Kodda, dosya adlarını değerler olarak kullanarak ve bağımsız değişkenlerini dahil etmek için çağrısında değişiklik (bu bağımsız değişkenler standart Python işleviyle aynı anlama `enable_attach` `certfile` `keyfile` `ssl.wrap_socket` sahiptir):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Aynı değişikliği yerel bilgisayarda kod dosyasında da değiştirebilirsiniz, ancak bu kod gerçekten çalıştırılamaysa da, kesinlikle gerekli değildir.

1. Uzak bilgisayarda Python programını yeniden başlatarak hata ayıklamaya hazır hale yükleyin.

1. Sertifikayı, sertifikayı Windows bilgisayarda Güvenilen Kök CA'ya ekleyerek kanalın güvenliğini Visual Studio:

    1. Sertifika dosyasını uzak bilgisayardan yerel bilgisayara kopyalayın.
    1. **Denetim Masası'i** açın ve Yönetimsel Araçlar Bilgisayar   >  **sertifikalarını yönetme'ye gidin.**
    1. Görüntülenen pencerede, sol  tarafta Güvenilen Kök Sertifika Yetkilileri'ı genişletin, Sertifikalar'a sağ **tıklayın** ve Tüm Görevleri İçeri **Aktar'ı**  >  **seçin.**
    1. uzak bilgisayardan kopyalanan *.cer* dosyasına gidin ve dosyayı seçin, ardından içeri aktarma işlemini tamamlamak için iletişim kutularına tıklayın.

1. Ekleme işlemini daha önce Visual Studio olarak, şimdi Bağlantı Hedefi (veya Niteleyici) protokolü olarak kullanarak yeniden `tcps://` **kullanın.** 

    ![SSL ile uzaktan hata ayıklama aktarımını seçme](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio SSL üzerinden bağlanırken karşılaşılan olası sertifika sorunları hakkında bilgi girmenizi sağlar. Uyarıları yoksayabilirsiniz ve devam edebilirsiniz, ancak kanal yine de dinlemeye karşı şifrelenmiş olsa da ortadaki adam saldırılarına açık olabilir.

    1. Aşağıda uzak **sertifikaya güvenilmiyor uyarısı görüyorsanız,** sertifikayı Güvenilir Kök CA'ya düzgün şekilde eklememişsiniz demektir. Bu adımları kontrol edin ve yeniden deneyin.

        ![SSL sertifikası güvenilen uyarısı](../../media/remote-debugging-ssl-warning.png)

    1. Uzak sertifika adının **konak** adı uyarısıyla eşleşmez olduğunu görüyorsanız, sertifikayı oluştururken Ortak Ad  olarak uygun ana bilgisayar adını veya IP adresini kullanmadınız demektir.

        ![SSL sertifikası ana bilgisayar adı uyarısı](../../media/remote-debugging-ssl-warning2.png)
