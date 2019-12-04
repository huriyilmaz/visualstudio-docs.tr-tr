---
title: ClickOnce ile COM bileşenleri dağıtma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c83367881b7ed6a69fe10af8b7c68eb1692e3e6
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706889"
---
# <a name="deploying-com-components-with-clickonce"></a>ClickOnce ile COM Bileşenleri Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eski COM bileşenlerinin dağıtımı, geleneksel olarak zor bir görevdir. Bileşenlerin Global olarak kaydedilmesi gerekir ve bu nedenle örtüşen uygulamalar arasında istenmeyen yan etkilere neden olabilir. Bileşenler bir uygulamaya tamamen yalıtılarak veya yan yana uyumlu olduğundan, bu durum genellikle .NET Framework uygulamalarında sorun değildir. Visual Studio, yalıtılmış COM bileşenlerini Windows XP veya daha yüksek işletim sisteminde dağıtmanıza olanak tanır.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .NET uygulamalarınızı dağıtmaya yönelik kolay ve güvenli bir mekanizma sağlar. Ancak, uygulamalarınız eski COM bileşenleri kullanıyorsa, bunları dağıtmak için ek adımlar gerçekleştirmeniz gerekir. Bu konu, yalıtılmış COM bileşenlerinin dağıtımını ve yerel bileşenlerin (örneğin, Visual Basic 6,0 veya Görseden C++) nasıl dağıtılacağını açıklar.  
  
 Yalıtılmış COM bileşenlerini dağıtma hakkında daha fazla bilgi için bkz. [ClickOnce Ile uygulama dağıtımını basitleştirme ve KAYıTSıZ com](/archive/msdn-magazine/2005/april/simplify-app-deployment-with-clickonce-and-registration-free-com).  
  
## <a name="registration-free-com"></a>Kayıt-ücretsiz COM  
 Kayıtsız com, yalıtılmış COM bileşenlerini dağıtmaya ve etkinleştirmeyle ilgili yeni bir teknolojidir. Bu, tipik olarak sistem kayıt defterine yüklenmiş olan tüm bileşenin tür kitaplığı ve kayıt bilgilerini, uygulama ile aynı klasörde depolanan bir XML dosyasına, bildirim olarak adlandırılan bir XML dosyasına yerleştirerek işe yarar.  
  
 Bir COM bileşenini yalıtmak, geliştiricinin makinesinde kaydedilmesini gerektirir, ancak son kullanıcının bilgisayarında kayıtlı olması gerekmez. Bir COM bileşenini yalıtmak için, tek yapmanız gereken, başvurusunun **yalıtılmış** özelliğini **doğru**olarak ayarladı. Varsayılan olarak, bu özellik, kayıtlı bir COM başvurusu olarak değerlendirilip değerlendirilmeyeceğini belirten **yanlış**olarak ayarlanır. Bu özellik **true**ise, derleme zamanında bu bileşen için bir bildirimin oluşturulmasına neden olur. Ayrıca, ilgili dosyaların yükleme sırasında uygulama klasörüne kopyalanmasına da neden olur.  
  
 Bildirim Oluşturucu yalıtılmış bir COM başvurusuyla karşılaştığında, bileşenin tür kitaplığındaki tüm `CoClass` girdilerini numaralandırır, her bir girdiyle ilgili kayıt verileriyle eşleşen ve tür kitaplığı dosyasındaki tüm COM sınıfları için bildirim tanımları oluşturuyor.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>ClickOnce kullanarak kayıtsız COM bileşenleri dağıtma  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım teknolojisi yalıtılmış COM bileşenleri dağıtmaya uygundur, çünkü hem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] hem de kayıtsız COM bileşeni, bir bileşenin dağıtılması için bir bildirime sahip olmasını gerektirir.  
  
 Genellikle, Bileşen yazarının bir bildirim sağlaması gerekir. Ancak, Visual Studio bir COM bileşeni için otomatik olarak bildirim oluşturma yeteneğine sahiptir. Bildirim oluşturma, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yayımlama işlemi sırasında gerçekleştirilir; daha fazla bilgi için bkz. [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md). Bu özellik ayrıca, Visual Basic 6,0 gibi önceki geliştirme ortamlarında yazdığınız eski bileşenlerden yararlanmanızı sağlar.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] COM bileşenlerini dağıtmanın iki yolu vardır:  
  
- COM bileşenlerinizi dağıtmak için önyükleyici kullanın; Bu, desteklenen tüm platformlarda kullanılabilir.  
  
- Yerel bileşen yalıtımı (kayıtsız COM olarak da bilinir) dağıtımı kullanın. Ancak, bu yalnızca Windows XP veya daha yüksek bir işletim sisteminde çalışır.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Basit bir COM bileşenini yalıtma ve dağıtmaya yönelik örnek  
 Kayıt-ücretsiz COM bileşeni dağıtımını göstermek için bu örnek, Visual Basic Visual Basic 6,0 kullanılarak oluşturulan yalıtılmış yerel bir COM bileşenine başvuran ve [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]kullanarak dağıtan Windows tabanlı bir uygulama oluşturur.  
  
 İlk olarak yerel COM bileşenini oluşturmanız gerekir:  
  
##### <a name="to-create-a-native-com-component"></a>Yerel bir COM bileşeni oluşturmak için  
  
1. Visual Basic 6,0 kullanarak, **Dosya** menüsünden **Yeni**ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda **Visual Basic** düğümünü SEÇIN ve bir **ActiveX DLL** projesi seçin. **Ad** kutusuna `VB6Hello`yazın.  
  
    > [!NOTE]
    > Kayıt-ücretsiz COM ile yalnızca ActiveX DLL ve ActiveX denetimi proje türleri desteklenir; ActiveX EXE ve ActiveX belge proje türleri desteklenmez.  
  
3. **Çözüm Gezgini**' de, **Class1. vb** ' ye çift tıklayarak metin düzenleyicisini açın.  
  
4. Class1. vb ' de `New` yöntemi için oluşturulan koddan sonra aşağıdaki kodu ekleyin:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. Bileşeni oluşturun. **Yapı** menüsünde **çözüm oluştur**' a tıklayın.  
  
> [!NOTE]
> Kayıt-ücretsiz COM yalnızca dll 'Leri ve COM denetimleri proje türlerini destekler. Kayıt-ücretsiz COM ile EXEs kullanamazsınız.  
  
 Artık Windows tabanlı bir uygulama oluşturabilir ve buna COM bileşenine bir başvuru ekleyebilirsiniz.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>COM bileşeni kullanarak Windows tabanlı bir uygulama oluşturmak için  
  
1. Visual Basic kullanarak, **Dosya** menüsünde, **Yeni**ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda **Visual Basic** düğümünü seçin ve **Windows uygulaması**' nı seçin. **Ad** kutusuna `RegFreeComDemo`yazın.  
  
3. **Çözüm Gezgini**, proje başvurularını görüntülemek Için **tüm dosyaları göster** düğmesini tıklatın.  
  
4. **Başvurular** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.  
  
5. **Başvuru Ekle** iletişim kutusunda, **Gözden** geçirme sekmesine tıklayın, VB6Hello. dll dosyasına gidin ve ardından seçin.  
  
    Başvurular listesinde bir **VB6Hello** başvurusu görüntülenir.  
  
6. **Araç kutusu**' nun üzerine gelin, bir **düğme** denetimi seçin ve onu **Form1** formuna sürükleyin.  
  
7. **Özellikler** penceresinde, düğmenin **Text** özelliğini **Hello**olarak ayarlayın.  
  
8. İşleyici kodu eklemek için düğmeye çift tıklayın ve kod dosyasında, işleyicinin aşağıdaki gibi okuduğu kodu ekleyin:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Uygulamayı çalıştırın. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.  
  
   Sonra, denetimi yalıtmanız gerekir. Uygulamanızın kullandığı her bir COM bileşeni, projenizde bir COM başvurusu olarak temsil edilir. Bu başvurular **Çözüm Gezgini** penceresindeki **Başvurular** düğümü altında görünür. ( **Proje** menüsünde **Başvuru Ekle** komutunu kullanarak doğrudan veya bir ActiveX denetimini formunuza sürükleyerek başvuru ekleyebildiğinize dikkat edin.)  
  
   Aşağıdaki adımlarda, COM bileşeninin nasıl yalıtılacağı ve yalıtılmış denetimi içeren güncelleştirilmiş uygulamayı nasıl yayımlayacağınız gösterilmektedir:  
  
##### <a name="to-isolate-a-com-component"></a>Bir COM bileşenini yalıtmak için  
  
1. **Çözüm Gezgini**, **Başvurular** düğümünde **VB6Hello** başvurusunu seçin.  
  
2. **Özellikler** penceresinde, **yalıtılmış** özelliğin değerini **false** değerinden **true**değerine değiştirin.  
  
3. **Yapı** menüsünde **çözüm oluştur**' a tıklayın.  
  
   Şimdi F5 tuşuna bastığınızda uygulama beklendiği gibi çalışır, ancak artık kayıtsız COM altında çalışmaktadır. Bunu kanıtlamak için, VB6Hello. dll bileşenini kaldırmayı ve RegFreeComDemo1. exe dosyasını Visual Studio IDE dışında çalıştırmayı deneyin. Düğmeye tıklandığında bu kez hala işe yarar. Uygulama bildirimini geçici olarak yeniden adlandırırsanız, yeniden başarısız olur.  
  
> [!NOTE]
> Geçici olarak kaydını kaldırarak bir COM bileşeni yokluğuna benzetim yapabilirsiniz. Bir komut istemi açın, `cd /d %windir%\system32`yazarak sistem klasörünüze gidin ve `regsvr32 /u VB6Hello.dll`yazarak bileşenin kaydını silin. `regsvr32 VB6Hello.dll`yazarak tekrar kaydedebilirsiniz.  
  
 Son adım [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]kullanarak uygulamayı yayımlamaktır:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Yalıtılmış bir COM bileşeniyle uygulama güncelleştirmesi yayımlamak için  
  
1. **Build** menüsünde, **RegFreeComDemo Yayımla**' ya tıklayın.  
  
    Yayımla Sihirbazı görüntülenir.  
  
2. Yayımla sihirbazında, yerel bilgisayarın diskinde yayımlanan dosyalara erişebileceğiniz ve bunları inceleyebileceğiniz bir konum belirtin.  
  
3. Uygulamayı yayımlamak için **son** ' a tıklayın.  
  
   Yayımlanan dosyaları incelerseniz, Sysmon. ocx dosyasının dahil edildiğini aklınızda olursunuz. Denetim, bu uygulamaya tamamen yalıtılmıştır, yani son kullanıcının makinesinde farklı bir denetim sürümü kullanan başka bir uygulama varsa, bu uygulamayla karışamaz.  
  
## <a name="referencing-native-assemblies"></a>Yerel derlemelere başvurma  
 Visual Studio, yerel Visual Basic 6,0 veya C++ derlemelere yönelik başvuruları destekler; Bu tür başvurular yerel başvurular olarak adlandırılır. **Dosya türü** özelliğinin **Yerel** veya **ActiveX**olarak ayarlandığını doğrulayarak başvurunun yerel olup olmadığını anlayabilirsiniz.  
  
 Yerel bir başvuru eklemek için **Başvuru Ekle** komutunu kullanın, ardından bildirime gidin. Bazı bileşenler, bildirimi DLL içine yerleştirir. Bu durumda, yalnızca DLL 'nin kendisini seçebilirsiniz ve Visual Studio, bileşenin gömülü bir bildirim içerdiğini algılarsa onu yerel bir başvuru olarak ekler. Visual Studio, başvurulan bileşenle aynı klasörseler de, bildirimde listelenen tüm bağımlı dosyaları veya derlemeleri otomatik olarak dahil eder.  
  
 COM denetim yalıtımı, zaten bildirimleri olmayan COM bileşenlerinin dağıtılmasını kolaylaştırır. Ancak, bir bileşen bir bildirim ile sağlandıysa bildirime doğrudan başvurabilirsiniz. Aslında, **yalıtılmış** özelliği kullanmak yerine bileşenin yazarı tarafından sağlanan bildirimi her zaman kullanmanız gerekir.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Kayıt-ücretsiz COM bileşeni dağıtımının sınırlamaları  
 Kayıtsız COM, geleneksel dağıtım teknikleri üzerinde açık avantajlar sağlar. Ancak, Ayrıca, dikkat edilecek bazı sınırlamalar ve uyarılar vardır. En büyük sınırlama yalnızca Windows XP veya üzeri sürümlerde kullanılabilir. Kaydolma ücretsiz COM uygulamasının uygulanması, bileşenleri çekirdek işletim sisteminde yüklü olan şekilde değişir. Ne yazık ki, kayıtsız COM için alt düzey destek katmanı yoktur.  
  
 Her bileşen kayıt için ücretsiz COM için uygun bir aday değildir. Aşağıdakilerden biri doğruysa bir bileşen uygun değildir:  
  
- Bileşen, işlem dışı bir sunucusudur. EXE sunucuları desteklenmez; yalnızca dll 'Ler desteklenir.  
  
- Bileşen işletim sisteminin bir parçasıdır veya XML, Internet Explorer veya Microsoft veri erişim bileşenleri (MDAC) gibi bir sistem bileşenidir. Bileşen yazarının yeniden dağıtım ilkesini izlemeniz gerekir; satıcınızla görüşün.  
  
- Bileşen, Microsoft Office gibi bir uygulamanın parçasıdır. Örneğin, Microsoft Excel nesne modelini yalıtmaya çalışmayın. Bu, Office 'in bir parçasıdır ve yalnızca tam Office ürününün yüklü olduğu bir bilgisayarda kullanılabilir.  
  
- Bileşen, bir eklenti veya bir ek bileşen olarak kullanılmak üzere tasarlanmıştır. Örneğin, bir Office eklentisi veya bir Web tarayıcısında bir denetim. Bu tür bileşenler genellikle, bildirim kapsamı ötesinde barındıran ortam tarafından tanımlanan bazı kayıt düzeni türlerini gerektirir.  
  
- Bileşeni, sistem için bir fiziksel veya sanal cihazı (örneğin, yazdırma biriktiricisi için bir cihaz sürücüsü) yönetir.  
  
- Bileşen, yeniden dağıtılabilen bir veri erişimidir. Veri uygulamaları, çalıştırılabilmesi için genellikle ayrı bir veri erişiminin yeniden dağıtılabilir olmasını gerektirir. Microsoft ADO veri denetimi, Microsoft OLE DB veya Microsoft veri erişimi bileşenleri (MDAC) gibi bileşenleri yalıtmak için denememelisiniz. Bunun yerine, uygulamanız MDAC veya SQL Server Express kullanıyorsa, bunları önkoşul olarak ayarlamanız gerekir; bkz. [nasıl yapılır: ClickOnce uygulaması Ile önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  Bazı durumlarda, bileşen geliştiricisi, kayıt açısından ücretsiz COM için yeniden tasarlayabilmesini sağlayabilir. Bu mümkün değilse, önyükleyici kullanarak standart kayıt düzeni aracılığıyla bunlara bağımlı olan uygulamalar oluşturmaya ve yayımlamaya devam edebilirsiniz. Daha fazla bilgi için bkz. [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  
  
  Bir COM bileşeni, uygulama başına yalnızca bir kez yalıtılabilir. Örneğin, aynı uygulamanın parçası olan iki farklı **sınıf kitaplığı** PROJESINDE aynı com bileşenini ayıramazsınız. Bunun yapılması, bir derleme uyarısına neden olur ve uygulama çalışma zamanında yükleme başarısız olur. Bu sorundan kaçınmak için, Microsoft COM bileşenlerini tek bir sınıf kitaplığında kapsüllemeyi önerir.  
  
  Uygulamanın dağıtımı kayıt gerektirmese de, geliştirici makinesinde COM kaydı yapılması gereken birkaç senaryo vardır. `Isolated` özelliği, derleme sırasında bildirimi otomatik oluşturmak için COM bileşeninin geliştiricinin makinesine kaydedilmesini gerektirir. Derleme sırasında kendi kendine kaydı çağıran bir kayıt yakalama özelliği yoktur. Ayrıca, tür kitaplığında açıkça tanımlanmayan tüm sınıflar bildirime yansıtılmaz. Yerel başvuru gibi önceden var olan bir bildirime sahip bir COM bileşeni kullanırken, bileşenin geliştirme zamanında kayıtlı olması gerekebilir. Ancak, bileşen bir ActiveX denetimi ise ve **araç kutusu** ve Windows Forms Tasarımcısına eklemek istiyorsanız kayıt gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Güvenliği ve Dağıtımı](../deployment/clickonce-security-and-deployment.md)
