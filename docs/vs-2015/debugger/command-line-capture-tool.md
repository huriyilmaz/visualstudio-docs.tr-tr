---
title: Komut satırı yakalama aracı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 208ff7f9bbfc2d07669a8b485edffc8dfc4cd54f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810005"
---
# <a name="command-line-capture-tool"></a>Komut Satırı Yakalama Aracı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe, grafik tanılama yakalama ve kayıttan yürütme için bir komut satırı aracıdır. Tüm özellik düzeylerinde Direct3D 12 aracılığıyla Direct3D 10 ' da desteklenir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parametreler  
 `-file` `filename`  
 Yakalama modu ( `-c` ) altında, `filename` grafik bilgilerinin kaydedildiği grafik günlük dosyasının adını belirtir. `filename`Belirtilmemişse, grafik bilgileri varsayılan olarak adlı bir dosyaya kaydedilir `<appname>-<date>-<time>.vsglog` .  
  
 Doğrulama (-v) modu altında, `filename` doğrulanacak grafik günlük dosyasının adını belirtir. `filename`Belirtilmemişse, son doğrulanan grafik günlüğü tekrar kullanılır.  
  
 `-frame` `frames`  
 Yakalama modu ' nun altında, `frames` yakalamak istediğiniz çerçeveleri belirtir. İlk kare 1 ' dir. Virgüller ve aralıklar kullanarak birden çok kare belirtebilirsiniz. Örneğin, ise, `frames` `2, 5, 7-9, 15` kareler `2` ,,,, `5` `7` `8` `9` ve `15` .  
  
 `-period` `periods`  
 Yakalama modu ' nun altında, `periods` kareleri yakalamak istediğiniz zaman aralıklarını saniye cinsinden belirtir. Virgüller ve aralıklar kullanarak birden çok nokta belirtebilirsiniz. Örneğin, `periods` ise, `2.1-5, 7.0-9.3` `2.1` ve `5` saniye arasında ve ile saniye arasında işlenen çerçeveler `7` `9.3` yakalanır.  
  
 `-manual`  
 Yakalama modu ' nun altında, `-manual` karelerin yazdırma ekranı tuşuna basılarak el ile yakalanacağını belirtir. Uygulama başlatıldığında çerçeveler yakalanabilir; çerçeveleri yakalamayı durdurmak için komut satırı arabirimine dönün ve ENTER tuşuna basın.  
  
 `-c` `app` [`args...`]  
 Yakalama modu. Yakalama modu ' nun altında, `app` grafik bilgilerini yakalamak istediğiniz uygulamanın adını belirtir; `args...` Bu uygulamaya ek komut satırı parametreleri belirtir.  
  
 `-p` [`filename`]  
 Kayıttan yürütme modu ( `-p` ). Kayıttan yürütme modu altında, `filename` oynatılacak grafik günlük dosyasının adını belirtir. `filename`Belirtilmemişse, en son çalınan grafik günlüğü tekrar kullanılır.  
  
 `-debug`  
 Kayıttan yürütme modu altında, `-debug` kayıttan yürütmenin Direct3D hata ayıklama katmanı etkinken gerçekleştirilmesi gerektiğini belirtir.  
  
 `-warp`  
 Kayıttan yürütme modu altında `-warp` Kayıttan YÜRÜTMENIN warp yazılım Oluşturucusu kullanılarak gerçekleştirilmesi gerektiğini belirtir.  
  
 `-hw`  
 Kayıttan yürütme modu altında, `-hw` Kayıttan YÜRÜTMENIN GPU donanımı kullanılarak gerçekleştirilmesi gerektiğini belirtir.  
  
 `-config`  
 Kayıttan yürütme modu altında, `-config` Bu bilgiler günlüğe kaydedilmişse, grafik günlük dosyasını yakalamak için kullanılan makine hakkındaki bilgileri görüntüler.  
  
 `-rawmode`  
 Kayıttan yürütme modu ' nun altında, `-rawmode` kayıttan yürütmenin kayıtlı olaylarda değişiklik yapılmadan gerçekleştirilmesi gerektiğini belirtir. Normal işlem altında kayıttan yürütme modu, hata ayıklamayı basitleştirmek ve kayıttan yürütmeyi hızlandırmak için kayıttan yürütmeye küçük değişiklikler yapabilir. Örneğin, takas zinciri komutlarının yürütülmesi yerine takas zinciri çıkışının benzetimini sağlayabilir. Genellikle bu bir sorun değildir, ancak kayıttan yürütmenin kayıtlı olaylara daha fazla cede oluşması için bir şekilde gerçekleşmesi gerekebilir; Örneğin, tam ekran işleme davranışını tam ekran modunda çalışırken yakalanan bir uygulamaya geri yüklemek için bu seçeneği kullanabilirsiniz.  
  
 `-toXML` [`xml_filename`]  
 Kayıttan yürütme modu altında `xml_filename` kayıttan yürütme XML gösteriminin yazıldığı dosyanın adını belirtir. `xml_filename`Belirtilmemişse, XML temsili, çalınan dosya ile aynı adlı bir dosyaya yazılır, ancak bir uzantı verilirler `.xml` .  
  
 `-v`  
 Doğrulama modu. Doğrulama modu ' nun altında, yakalanan çerçeveler hem donanım hem de ÇARPıTMA üzerinde oynatılır ve sonuçları bir görüntü karşılaştırma işlevi kullanılarak karşılaştırılır. Bu özelliği kullanarak, işleinizi etkileyen sürücü sorunlarını hızla belirleyebilirsiniz.  
  
 `-examine` `events`  
 Doğrulama modu ' nun altında, `events` acil sonuçları karşılaştırılan grafik olaylarının kümesini belirtir. Örneğin, `-examine present,draw,copy,clear` karşılaştırmayı yalnızca bu kategorilere ait olaylarla sınırlandırır.  
  
> [!TIP]
> `-examine present,draw,copy,clear`Bu işlem, birçok sorunu ortaya çıkardığı ve daha kapsamlı bir olay kümesinden daha az zaman alacak olduğundan, ' den başlayıp başlamadan önce. Gerekirse, bu olayları doğrulamak ve diğer sorun türlerini açığa çıkarmak için daha büyük veya farklı bir olay kümesi belirtebilirsiniz.  
  
 `-haltonfail`  
 Doğrulama modu altında, `-haltonfail` donanım ve çarpıtma işleyicisi arasında farklılıklar algılandığında doğrulamayı durdurur. Bir anahtara basıldığında doğrulama devam eder.  
  
 `-exitonfail`  
 Doğrulama modu altında, `-exitonfail` donanım ve çarpıtma işleyicisi arasında farklılıklar algılandığında doğrulamadan hemen çıkar. Program bu şekilde çıktığında `0` ortama döner; Aksi takdirde döndürür `1` .  
  
 `-showprogress`  
 Doğrulama modu altında `-showprogress` doğrulama oturumuyla ilgili ilerleme bilgilerini görüntüler. ÇARPıTMA ilerlemesi solda görüntülenir; donanım ilerlemesi sağ tarafta görüntülenir.  
  
 `-e` `search_string`  
 Yüklü Windows Mağazası uygulamalarını numaralandırır. Bu bilgileri, Windows Mağazası uygulamalarıyla komut satırı yakalamaları gerçekleştirmek için kullanabilirsiniz.  
  
 `-info`  
 Makine ve yakalama dll 'Leri hakkındaki bilgileri görüntüler.  
  
## <a name="remarks"></a>Açıklamalar  
 DXCap.exe üç modda çalışır:  
  
 Yakalama modu (-c)  
 Çalışan bir uygulamadan grafik bilgilerini yakalayın ve bir grafik günlük dosyasına kaydedin. Yakalama özellikleri ve dosya biçimi, Visual Studio ile aynıdır.  
  
 Kayıttan yürütme modu (-p)  
 Mevcut bir grafik günlük dosyasından daha önce yakalanan grafik olaylarını kayıttan yürütün. Varsayılan olarak, grafik günlük dosyası tam bir uygulamadan yakalansa bile kayıttan yürütme bir pencerede gerçekleşir. Kayıttan yürütme işlemi, yalnızca grafik günlük dosyası tam ekran uygulamadan yakalandıysa ve belirtildiğinde tam ekranda gerçekleşir `–rawmode` .  
  
 Doğrulama modu ( `-v` )  
 Yakalanan çerçeveleri her iki donanımda ve çarpmaya oynatarak ve sonra sonuçlarını bir görüntü karşılaştırma işlevi kullanarak karşılaştırarak işleme davranışını doğrular. Bu özelliği kullanarak, işleinizi etkileyen sürücü sorunlarını hızla belirleyebilirsiniz.  
  
 Bu modların yanı sıra, dxcap.exe grafik bilgilerini yakalama veya kayıttan yürütme gerçekleştirmeyen iki diğer işlev de gerçekleştirir.  
  
 Enumeration işlevi ( `-e` )  
 Makinede yüklü olan Windows Mağazası uygulamaları hakkındaki ayrıntıları görüntüler. Bu ayrıntılar, Windows Mağazası uygulamasında yürütülebilir dosyayı tanımlayan paket adı ve AppID 'yi içerir. DXCap.exe kullanarak bir Windows Mağazası uygulamasından grafik bilgilerini yakalamak için, bir masaüstü uygulaması yakaladığınızda kullanılan yürütülebilir dosya adı yerine paket adı ve AppID 'yi kullanın.  
  
 Info işlevi (`-info)`  
 Makine ve yakalama dll 'Leri hakkındaki ayrıntıları görüntüler.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Bir masaüstü uygulamasından grafik bilgilerini yakalama  
 `–c`Grafik bilgilerini yakalamak istediğiniz uygulamayı belirtmek için kullanın.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Grafik bilgileri varsayılan olarak adlı bir dosyaya kaydedilir `<appname>-<date>-<time>.vsglog` . `–file`Uygulamasına kaydedilecek farklı bir dosya belirtmek için kullanın.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Uygulamanın dosya adından sonra dahil ederek yakaladığınız uygulamaya yönelik ek komut satırı parametreleri belirtin.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Yukarıdaki örnekteki komut, 3-b içeriğini işlemek için WebGL API 'sini kullanan www.fishgl.com adresinde bulunan Web sayfasını görüntülerken, Internet Explorer 'ın masaüstü sürümünden grafik bilgilerini yakalar.  
  
> [!NOTE]
> Uygulamadan sonra görüntülenen komut satırı bağımsız değişkenleri, seçeneğini kullanmadan önce DXCap.exe için tasarlanan bağımsız değişkenleri belirtmeniz gerekir `–c` .  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Bir Windows Mağazası uygulamasında grafik bilgilerini yakalayın.  
 Bir Windows Mağazası uygulamasında grafik bilgilerini yakalayabilirsiniz.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Windows Mağazası uygulamasından yakalamak için DXCap.exe kullanmak, Windows masaüstü uygulamasından yakalamak için kullanmaya benzer, ancak bunun yerine bir masaüstü uygulamasını dosya adına göre tanımlayarak, paket adına göre bir Windows Mağazası uygulamasını ve bu paketin içinde yakalamak istediğiniz yürütülebilir dosyanın adını veya KIMLIĞINI belirlersiniz. Makinenizde yüklü olan Windows Mağazası uygulamalarını nasıl tanımlayabileceğinizi daha kolay hale getirmek için, bu `–e` seçeneği listelemek üzere DXCap.exe kullanın:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Aradığınız uygulamayı bulmaya yardımcı olması için isteğe bağlı bir arama dizesi sağlayabilirsiniz. Arama dizesi sağlandığında, paket adı, uygulama adı veya uygulama kimlikleri arama dizesiyle eşleşen Windows Mağazası uygulamalarını numaralandırır DXCap.exe. Arama büyük/küçük harfe duyarlıdır.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Yukarıdaki komutta, "map" ile eşleşen Windows Mağazası uygulamaları numaralandırılır; çıktı şöyledir:  
  
 **"Microsoft. BingMaps" paketi:**  
 **InstallDirectory: C:\Program Files\WindowsApps\Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Ad: Microsoft. BingMaps**  
 **Yayımcı: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Sürüm: 2.1.2914.1734**  
 **Başlatılabilir uygulamalar:**  
 **Kimlik: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IWWA: Hayır**  
 **Appspec (başlatmak için): DXCap.exe-c Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe, AppexMaps** Her numaralandırılmış uygulama için çıktının son satırı, grafik bilgilerini buradan yakalamak için kullanabileceğiniz komutu görüntüler.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Belirli saatler arasında belirli çerçeveler veya çerçeveler yakalayın.  
 `–frame`Virgüller ve aralıklar kullanarak yakalamak istediğiniz çerçeveleri belirtmek için kullanın:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Ya da `–period` çerçeve yakalamak için bir zaman aralığı kümesi belirtmek için kullanın. Zaman aralıkları saniye cinsinden belirtilir ve birden çok Aralık belirtilebilir:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Çerçeveleri etkileşimli olarak yakalayın.  
 `–manual`Çerçeveleri etkileşimli olarak yakalamak için kullanın. Yakalamayı başlatmak için ENTER tuşuna basın ve durdurmak için ENTER tuşuna basın.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Grafik günlüğü dosyasını kayıttan yürütme  
 `-p`Daha önce yakalanan bir grafik günlük dosyasını kayıttan yürütmek için kullanın.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 En son yakalanan grafik günlüğünü çalmak için dosya adını bırakın.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Ham modda kayıttan çal  
 `-rawmode`Yakalanan komutları tam olarak oluşan şekilde kayıttan yürütmek için kullanın. Normal kayıttan yürütme altında bazı komutlar öykünülecektir, örneğin, tam ekran uygulamasından yakalanan bir grafik günlüğü dosyası bir pencerede yeniden oynatılır; ham mod etkinken, aynı dosya tam ekranda kayıttan yürütmeye çalışacaktır.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP veya donanım cihazı kullanarak kayıttan yürütme  
 Bir donanım cihazında yakalanan bir grafik günlüğü dosyasını, WARP kullanacak şekilde yürütmeye zorlamak veya WARP üzerinde yakalanan bir günlüğün bir donanım cihazı kullanmak için yürütülmesini zorlamak isteyebilirsiniz. `-warp`Warp kullanarak kayıttan yürütmek için kullanın.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 `-hw`Donanım kullanarak kayıttan yürütmek için kullanın.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Bir grafik günlük dosyasını ÇARPıTıP doğrulama  
 Doğrulama modu altında, grafik günlük dosyası hem donanım hem de ÇARPıTMA üzerinde oynatılır ve sonuçları karşılaştırılır. Bu, sürücünün neden olduğu işleme hatalarını belirlemenize yardımcı olabilir. Grafik donanımının ÇARPMANıN doğru davranışını doğrulamak için – v kullanın.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Karşılaştırma miktarını azaltmak için, doğrulamanın karşılaştırılacağı ve diğer komutların yoksayılacağı komutların bir alt kümesini belirtebilirsiniz. Sonuçları karşılaştırmak istediğiniz komutları belirtmek için-İncele kullanın.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Grafik günlük dosyasını png 'lere Dönüştür  
 Grafikleri bir grafik günlük dosyasından görüntülemek veya analiz etmek için DXCap.exe yakalanan çerçeveleri. png (Taşınabilir Ağ Grafikleri) resim dosyaları olarak kaydedebilir. `-screenshot`Yakalanan çerçeveleri. png dosyaları olarak çıktısını almak için kayıttan yürütme modunda ' i kullanın.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 `–frame` `–screenshot` Çıktısını almak istediğiniz çerçeveleri belirtmek için ile kullanın.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Grafik günlük dosyasını XML 'e dönüştürme  
 FindStr veya XSLT gibi tanıdık araçları kullanarak grafik günlüklerini işlemek ve analiz etmek için DXCap.exe bir grafik günlük dosyasını XML 'e dönüştürebilir. `-toXML`Kayıttan yürütmek yerine, günlüğü XML 'e dönüştürmek için kayıttan yürütme modunda kullanın.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Varsayılan olarak, XML çıktısı grafik günlüğü ile aynı ada sahip bir dosyaya yazılır, ancak buna bir. xml uzantısı verilir. Yukarıdaki örnekte, XML dosyası **regression_test_12.xml**olarak adlandırılır. XML dosyasına farklı bir ad vermek için, daha sonra belirtin `-toXML` .  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Elde edilen dosya şuna benzer bir XML içerir:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Gereksinimler
