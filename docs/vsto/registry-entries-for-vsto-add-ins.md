---
title: VSTO Eklentileri için kayıt defteri girişleri
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416529"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO Eklentileri için kayıt defteri girişleri
  Visual Studio kullanılarak oluşturulan VSTO Eklentileri dağıtırken belirli bir kayıt defteri girişi kümesi oluşturmanız gerekir. Bu kayıt defteri girişleri, Microsoft Office uygulamasının VSTO Eklentisini keşfetmesini ve yüklemesini sağlayan bilgiler sağlar.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Projenizi oluşturduğunuzda, Visual Studio, VSTO Eklentisini kolayca çalıştırıp hata ayıklamanız için geliştirme bilgisayarında bu kayıt defteri girişlerini oluşturur. VSTO Eklentinizi dağıtmak için ClickOnce'yi kullanırsanız, kayıt defteri girişleri otomatik olarak son kullanıcı bilgisayarında oluşturulur. VSTO Eklentinizi dağıtmak için Windows Installer kullanıyorsanız, son kullanıcı bilgisayarında kayıt defteri girişlerini oluşturmak için InstallShield Limited Edition projesini yapılandırmanız gerekir.

 VSTO Eklentileri için yükleme işlemi sırasında kayıt defteri girişlerinin nasıl kullanıldığı hakkında daha fazla bilgi için [VSTO Eklentilerinin Mimarisi'ne](../vsto/architecture-of-vsto-add-ins.md)bakın.

> [!NOTE]
> Bu konuda, metin *eklenti kimliği* VSTO Eklentiniz için benzersiz bir kimliği temsil eder. Varsayılan olarak, kimlik VSTO Eklenti derlemenizin adıdır.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Geçerli kullanıcı ve tüm kullanıcılar için VSTO Eklentilerini kaydedin
 VSTO Eklentisi yüklendiğinde, iki şekilde kaydedilebilir:

- Yalnızca geçerli kullanıcı için (diğer bir deyişle, yalnızca VSTO Eklentisi yüklendiğinde bilgisayarda oturum açan kullanıcı tarafından kullanılabilir). Bu durumda, kayıt defteri girişleri **HKEY_CURRENT_USER**altında oluşturulur.

- Tüm kullanıcılar için (diğer bir deyişle, bilgisayarda oturum açan herhangi bir kullanıcı VSTO Eklentisi'ni kullanabilir). Bu durumda, kayıt defteri girişleri **HKEY_LOCAL_MACHINE**altında oluşturulur.

  Visual Studio'yu kullanarak oluşturduğunuz tüm VSTO Eklentileri geçerli kullanıcı için kaydedilebilir. Ancak, VSTO Eklentileri yalnızca belirli senaryolarda tüm kullanıcılar için kaydedilebilir. Bu senaryolar, Microsoft Office'in bilgisayardaki sürümüne ve VSTO Eklentisinin nasıl dağıtıldığuna bağlıdır.

### <a name="deployment-type"></a>Dağıtım türü
 VSTO Eklentisi dağıtmak için ClickOnce'yi kullanırsanız, VSTO Eklentisi yalnızca geçerli kullanıcı için kaydedilebilir. Bunun nedeni ClickOnce'nin yalnızca **HKEY_CURRENT_USER**altında anahtar oluşturmayı desteklemesidir. Bir bilgisayardaki tüm kullanıcılara VSTO Eklentisi kaydetmek istiyorsanız, VSTO Eklentisini dağıtmak için Windows Installer'ı kullanmanız gerekir. Bu dağıtım türleri hakkında daha fazla bilgi için [ClickOnce'i kullanarak Bir Office çözümlerini dağıt'a](../vsto/deploying-an-office-solution-by-using-clickonce.md) bakın ve [Windows Installer'ı kullanarak bir Office çözümlerini dağıtın.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="registry-entries"></a>Kayıt defteri girdileri
 Gerekli VSTO Eklenti kayıt defteri girişleri, yüklemenin geçerli kullanıcı veya tüm **HKEY_LOCAL_MACHINE** kullanıcılar için olup olmadığının bağlı olarak **Root'un HKEY_CURRENT_USER** veya HKEY_LOCAL_MACHINE aşağıdaki kayıt defteri anahtarlarının altında yer alır. *Root*

|Ofis Başvurusu|Yapılandırma Yolu|
|------------------|------------------|
|Visio|*Kök*\Yazılım\Microsoft\\*Visio*\Addins\\eklenti*kimliği*|
|Diğer Tüm|*Root*\\\Software\Microsoft\Office*Office uygulama*adı\\\Addins*eklenti kimliği*|

> [!NOTE]
> Yükleyici 64 bit Windows'daki tüm kullanıcıları hedefliyorsa, biri HKEY_LOCAL_MACHINE\Software\Microsoft ve diğeri HKEY_LOCAL_MACHINE\Software\\**WOW6432Node**\Microsoft kovanı altında olmak üzere iki kayıt defteri girişi içermeniz önerilir. Bunun nedeni, kullanıcıların Office'in 32 bit veya 64 bit sürümlerini bilgisayarda kullanmalarının mümkün olmasıdır.
>
>Yükleyici geçerli kullanıcıyı hedefliyorsa, HKEY_CURRENT_USER\Yazılım yolu paylaşıldığından WOW6432Node'a yüklenmesi gerekmez.
>
>Daha fazla bilgi için lütfen [Kayıt Defteri'nde 32 bit ve 64 bit Uygulama Verileri'ne](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry) bakın

 Aşağıdaki tabloda bu kayıt defteri anahtarının altındaki girişler listelenebaltındadır.

|Girdi|Tür|Değer|
|-----------|----------|-----------|
|**Açıklama**|REG_SZ|Gereklidir. VSTO Eklentisi'nin kısa bir açıklaması.<br /><br /> Bu açıklama, kullanıcı Microsoft Office uygulamasındaseçenekler **iletişim** kutusunun **Eklentiler** bölmesinde VSTO Eklentisi'ni seçtiğinde görüntülenir.|
|**Friendlyname**|REG_SZ|Gereklidir. Microsoft Office uygulamasındaki **COM Eklentileri** iletişim kutusunda görüntülenen VSTO Eklentisi'nin açıklayıcı adı. Varsayılan değer VSTO Eklenti Kimliği'dir.|
|**Loadbehavior**|REG_DWORD|Gereklidir. Uygulama VSTO Eklentisini yüklemeye çalıştığında ve VSTO Eklentisinin (yüklü veya boşaltılmış) geçerli durumunu belirten bir değer.<br /><br /> Varsayılan olarak, bu giriş 3 olarak ayarlanır ve bu giriş, VSTO Eklentisinin başlangıçta yüklendiğini belirtir. Daha fazla bilgi için [LoadBehavior değerlerine](#LoadBehavior)bakın. **Not:**  Bir kullanıcı VSTO Eklentisini devre dışı ederse, bu eylem **HKEY_CURRENT_USER** kayıt defteri kovanındaki **LoadBehavior** değerini değiştirir. Her kullanıcı için, HKEY_CURRENT_USER kovandaki **LoadBehavior** değerinin **değeri, HKEY_LOCAL_MACHINE** kovan'da tanımlanan varsayılan **LoadBehavior'ı** geçersiz kılar.|
|**Bildirim**|REG_SZ|Gereklidir. VSTO Eklentisi için dağıtım bildiriminin tam yolu. Yol, yerel bilgisayarda bir konum, ağ paylaşımı (UNC) veya bir Web sunucusu (HTTP) olabilir.<br /><br /> Çözümü dağıtmak için Windows Installer kullanıyorsanız, önekfile:/// **bildirim** yoluna eklemeniz gerekir. **file:///** Ayrıca bu yolun sonuna **kadar vstolocal&#124;** dize (yani,&#124;**vstolocal)** **takip** edilen boru karakteri ni de eklemelisiniz. Bu, çözümünüzün ClickOnce önbelleği yerine yükleme klasöründen yüklenmesini sağlar. Daha fazla bilgi için bkz. Windows [Installer'ı kullanarak Bir Office çözümlerini dağıtın.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md) **Not:**  Geliştirme bilgisayarında bir VSTO Eklentisi oluşturduğunuzda, Visual Studio bu kayıt defteri girişine **&#124;vstolocal** dizesini otomatik olarak ekler.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Outlook form bölgeleri için kayıt defteri girişleri
 Outlook için VSTO Eklentisi'nde özel bir form bölgesi oluşturursanız, form bölgesini Outlook'a kaydetmek için ek kayıt defteri girişleri kullanılır. Bu girişler, form bölgesinin desteklediği her ileti sınıfı için farklı bir kayıt defteri anahtarı altında oluşturulur. Bu kayıt defteri anahtarları, *Root'un* **HKEY_CURRENT_USER** veya **HKEY_LOCAL_MACHINE**olduğu aşağıdaki konumdadır.

 *Kök*\Yazılım\Microsoft\Office\Outlook\FormBölgeler\\*ileti sınıfı*

 Tüm VSTO Eklentileri tarafından paylaşılan diğer kayıt defteri girişleri gibi Visual Studio da projenizi oluştururken geliştirme bilgisayarında form bölge kayıt defteri girişlerini oluşturur. VSTO Eklentinizi dağıtmak için ClickOnce'yi kullanırsanız, kayıt defteri girişleri otomatik olarak son kullanıcı bilgisayarında oluşturulur. VSTO Eklentinizi dağıtmak için Windows Installer kullanıyorsanız, son kullanıcı bilgisayarında kayıt defteri girişlerini oluşturmak için InstallShield Limited Edition projesini yapılandırmanız gerekir.

 Form bölgesi kayıt defteri girişleri hakkında daha fazla bilgi için [bkz.](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form) Outlook form bölgeleri hakkında daha fazla bilgi için [bkz.](../vsto/creating-outlook-form-regions.md)

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>LoadBehavior değerleri
 *Root*\\\Software\Microsoft\Office*uygulama adı*\Addins\\*add-in ID* tuşu altında **LoadBehavior** girişi, VSTO Eklentisi'nin çalışma süresi davranışını belirten değerlerin bitwise birleşimini içerir. En düşük sipariş biti (0 ve 1 değerleri) VSTO Eklentisinin şu anda yüklenip yüklenmediğini veya yüklenmediğini gösterir. Diğer bitler, uygulamanın VSTO Eklentisini yüklemeye çalıştığında bunu gösterir.

 Genellikle, **LoadBehavior** girişi, VSTO Eklentisi son kullanıcı bilgisayarlarına yüklendiğinde 0, 3 veya 16 (ondalık olarak) olarak ayarlanacak şekilde tasarlanmıştır. Varsayılan olarak Visual Studio, vsto Eklentinizin **LoadBehavior** girişini oluştururken veya yayımladığınızda 3 olarak ayarlar.

 Aşağıdaki **tablo, LoadBehavior** girişinin tüm olası değerlerini listeler. Bu tablodaki bazı açıklamalar, VSTO Eklentisi'nin el ile veya programlı olarak yüklenmesianlamına geliyor. VSTO Eklentisini el ile yüklemek için, uygulamadaki **COM Eklentileri** iletişim kutusunda KI VSTO Eklentisi'nin yanındaki onay kutusunu seçin. VSTO Eklentisini programlı olarak yüklemek için, VSTO Eklentisini temsil eden <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> <xref:Microsoft.Office.Core.COMAddIn> nesnenin özelliğini **doğru**olarak ayarlayın.

|Değer (ondalık olarak)|VSTO Eklenti durumu|VSTO Eklenti yükü davranışı|Açıklama|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Kaldırıldı|Otomatik olarak yüklemeyin|Uygulama asla VSTO Eklentisini otomatik olarak yüklemeye çalışmaz. Kullanıcı VSTO Eklentisini el ile yüklemeyi deneyebilir veya VSTO Eklentisi programlı olarak yüklenebilir.<br /><br /> VSTO Eklentisi başarıyla yüklenirse, **LoadBehavior** değeri 0 kalır, ancak **COM Eklentileri** iletişim kutusundaki VSTO Eklentisi'nin durumu VSTO Eklentisinin yüklendiğini gösterecek şekilde güncelleştirilir.|
|1|Yüklü|Otomatik olarak yüklemeyin|Uygulama asla VSTO Eklentisini otomatik olarak yüklemeye çalışmaz. Kullanıcı VSTO Eklentisini el ile yüklemeyi deneyebilir veya VSTO Eklentisi programlı olarak yüklenebilir.<br /><br /> COM **Eklentileri** iletişim kutusu, vsto eklentisinin uygulama başladıktan sonra yüklendiğini belirtse de, VSTO Eklentisi el ile veya programlı olarak yüklenene kadar yüklenmez.<br /><br /> Uygulama VSTO Eklentisini başarıyla yüklerse, **LoadBehavior** değeri 0'a dönüşür ve uygulama kapandıktan sonra 0'da kalır.|
|2|Kaldırıldı|Başlangıçta yük|Uygulama VSTO Eklentisini otomatik olarak yüklemeye çalışmaz. Kullanıcı VSTO Eklentisini el ile yüklemeyi deneyebilir veya VSTO Eklentisi programlı olarak yüklenebilir.<br /><br /> Uygulama VSTO Eklentisini başarıyla yüklerse, **LoadBehavior** değeri 3'e dönüşür ve uygulama kapandıktan sonra 3'te kalır.|
|3|Yüklü|Başlangıçta yük|Uygulama başlatıldığında VSTO Eklentisi'ni yüklemeye çalışır. Visual Studio'da bir VSTO Eklentisi oluşturduğunuzda veya yayımladığınızda varsayılan değer budur.<br /><br /> Uygulama VSTO Eklentisini başarıyla yüklerse, **LoadBehavior** değeri 3 kalır. VSTO Eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 2'ye dönüşür ve uygulama kapandıktan sonra 2'de kalır.|
|8|Kaldırıldı|İsteğe bağlı yük|Uygulama VSTO Eklentisini otomatik olarak yüklemeye çalışmaz. Kullanıcı VSTO Eklentisini el ile yüklemeyi deneyebilir veya VSTO Eklentisi programlı olarak yüklenebilir.<br /><br /> Uygulama VSTO Eklentisini başarıyla yüklerse, **LoadBehavior** değeri 9'a dönüşür.|
|9|Yüklü|İsteğe bağlı yük|VSTO Eklentisi, kullanıcının VSTO Eklentisi'nde işlevsellik kullanan bir Kullanıcı Arabirimi öğesini (örneğin Şerit'teki özel bir düğme) tıklatması gibi yalnızca uygulama gerektirdiğinde yüklenir.<br /><br /> Uygulama VSTO Eklentisini başarıyla yüklerse, **LoadBehavior** değeri 9 kalır, ancak **COM Eklentileri** iletişim kutusundaki VSTO Eklentisi'nin durumu güncelleştirilir ve VSTO Eklentisi'nin şu anda yüklendiğini gösterir. VSTO Eklentisi yüklenirken bir hata oluşursa, **LoadBehavior** değeri 8'e dönüşür.|
|16|Yüklü|İlk kez yükleyin, sonra isteğe bağlı yükleyin|VSTO Eklentinizin isteğe bağlı olarak yüklenmesini istiyorsanız bu değeri ayarlayın. Kullanıcı uygulamayı ilk kez çalıştırdığında uygulama VSTO Eklentisini yükler. Kullanıcı uygulamayı bir sonraki çalıştırdığında, uygulama VSTO Eklentisi tarafından tanımlanan kullanıcı arabirimi öğelerini yükler, ancak kullanıcı VSTO Eklentisi ile ilişkili bir Kullanıcı Ara Birimi öğesini tıklatana kadar VSTO Eklentisi yüklenmez.<br /><br /> Uygulama VSTO Eklentisini ilk kez başarıyla yüklediğinde, VSTO Eklentisi yüklenirken **LoadBehavior** değeri 16 kalır. Uygulama kapandıktan sonra **LoadBehavior** değeri 9'a dönüşür.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office çözümlerini dağıtma](../vsto/deploying-an-office-solution.md)
 