---
title: Hata ayıklayıcısında kesme noktaları sorunlarını | Microsoft Docs
description: Kesme noktası devre dışı bırakılırsa veya ayarlenemiyorsa boş daire olarak görüntülenir. Kesme noktaları ayarlarken ortaya çıkabilir sorunlar hakkında bilgi için buraya bakın.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2ef3445c45eb56e3f787522eb4d0fa076e2781875af2ea35a301515e91b15c16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310926"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio Debugger'da Kesme Noktaları sorunlarını giderme

## <a name="breakpoint-warnings"></a>Kesme Noktası Uyarıları

Hata ayıklama sırasında kesme noktası iki olası görsel eyalete sahip olur: düz kırmızı daire ve boş (beyaz dolgulu) daire. Hata ayıklayıcısı hedef işlemde başarıyla bir kesme noktası ayarlayabilecekse, düz kırmızı bir daire kalır. Kesme noktası boş bir daire ise kesme noktası devre dışı bırakılır veya kesme noktası ayarlanırken uyarı oluştu. Farkı belirlemek için kesme noktası üzerine gelin ve bir uyarı olup olmadığını bakın.

Aşağıdaki iki bölümde önemli uyarılar ve nasıl düzeltilenler açıklanmaktadır.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Bu belge için simge yüklenmedi"

Modüller **penceresine** (**Modüllerde**  >  **hata Windows**) gidin ve  >  modülün yüklü olup olmadığını kontrol edin.
* Modülün yüklü olması durumunda Sembollerin yük **olup** olmadığını görmek için Sembol Durumu sütununu kontrol edin.
  * Semboller yüklenmezse sorunu tanılamak için sembol durumunu kontrol edin. Modüller penceresindeki bir modülün bağlam **menüsünden** Sembol Yükleme **Bilgileri...** seçeneğine tıklar ve hata ayıklayıcının sembolleri yüklemek için nereye baktığını görebilirsiniz. Sembolleri yükleme hakkında daha fazla bilgi için [bkz. Sembol Belirtme (.pdb) ve Kaynak Dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
  * Semboller yüklenirse, PDB kaynak dosyalarınız hakkında bilgi içermez. Bunların birkaç olası nedeni vardır:
    * Kaynak dosyalarınız yakın zamanda eklendiyse modülün güncel bir sürümünün yükleniyor olduğunu onaylayın.
    * /PDBSTRIPPED bağlantı seçeneği kullanılarak **çıkarılmış PDB'ler** oluşturmak mümkündür. Çıkarılmış PDB'ler kaynak dosya bilgilerini içermez. Şeritli PDB ile değil, tam PDB ile çalıştığınızı onaylayın.
    * PDB dosyası kısmen bozuk. Sorunu çözmeyi denemek için dosyasını silin ve modülün temiz bir derlemesini gerçekleştirin.

* Modülüniz yüklenmemişse, nedenini bulmak için aşağıdakini kontrol edin:
  * Doğru işlemde hata ayıklarken onaylayın.
  * Doğru tür kodda hata ayıklarken hata ayıklayalıp denetlemeyebilirsiniz. İşlemler penceresinde hata ayıklamak için hata ayıklayıcının yapılandırılan kod türünü **bulabilirsiniz**( İşlemler'de   >  **Windows**  >  **ayıkla).** Örneğin, C# kodunda hata ayıklamaya çalışıyorsanız, hata ayıklayıcının uygun tür ve .NET sürümü için yapılandırıldığından emin olun (örneğin, Yönetilen (v4 ) ve \* Yönetilen (v2 \* /v3 ) ve Yönetilen \* (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… geçerli kaynak kodu yerleşik sürümünden farklı..."

Bir kaynak dosya değişmişse ve kaynak artık hata ayıklamakta olduğunuz kodla eşleyene kadar, hata ayıklayıcı varsayılan olarak kodda kesme noktaları ayarlamaz. Normalde bu sorun bir kaynak dosya değiştiriken ancak kaynak kod yeniden oluşturulmuşsa gerçekleşir. Bu sorunu düzeltmek için projeyi yeniden oluşturma. Derleme sistemi, projenin güncel olmadığını düşünüyorsa, kaynak dosyayı yeniden kaydederek veya derlemeden önce projenin derleme çıkışını temizerek proje sistemini yeniden derlemeye zorabilirsiniz.

Nadir senaryolarda, eşleşen kaynak koduna sahip olmadan hata ayıklamak istemeyebilirsiniz. Kaynak kodu eşleştirmeden hata ayıklama kafa karıştırıcı bir hata ayıklama deneyimine neden olabilir, bu nedenle devam etmek istediğinizden emin olun.

Bu güvenlik denetimlerini devre dışı bırakmak için, aşağıdakilerden birini yapın:
* Tek bir kesme noktası değiştirmek için düzenleyicide kesme noktası simgesinin üzerine gelin ve ayarlar (dişli) simgesine tıklayın. Düzenleyiciye bir göz atma penceresi eklenir. Göz atma penceresinin en üstünde kesme noktası konumunu belirten bir köprü vardır. Kesme noktası konumunun değiştirilmesine izin vermek için köprüye tıklayın ve Kaynak kodun özgün koddan farklı olmasına **izin ver'i seçin.**
* Tüm kesme noktaları için bu ayarı değiştirmek için Hata Ayıklama Seçenekleri'ne gidin  >  **ve Ayarlar.** Hata **Ayıklama/Genel sayfasında,** Özgün sürümle **tam olarak eşan kaynak dosyaları gerektir seçeneğinin temizlemesi** gerekir. Hata ayıklamayı bitirdikten sonra bu seçeneği yeniden kullanılabilir hale geldiğinden emin olun.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Kesme noktası başarıyla ayarlanmış (uyarı yok) ama isabet etmedi

Bu bölüm, hata ayıklayıcı herhangi bir uyarı görüntülemezken sorunları gidermeye ilişkin bilgiler sağlar. Kesme noktası etkin bir şekilde hata ayıklarken düz kırmızı bir dairedir ancak kesme noktası isabet etmese de.

Denetlememiz gereken birkaç şey vardır:
1. Kodunuz birden fazla işlemde veya birden fazla bilgisayarda çalışıyorsa, doğru işlemde veya bilgisayarda hata ayıklarken emin olun.
2. Kodunuzun çalıştırılı olduğunu onaylayın. Kodunuzun çalışacağını test etmek için kesme noktası ayarlamaya ve ardından projenizi yeniden oluşturmaya çalıştığınız kod satırına `System.Diagnostics.Debugger.Break` `__debugbreak` (C#/VB) veya (C++) çağrısı ekleyin.
3. İyileştirilmiş kodda hata ayıklaması yapılıyorsa kesme noktanın ayar bulunduğu işlevin başka bir işleve altı çizili olarak ayarlanmay olduğundan emin olun. Önceki `Debugger.Break` denetimde açıklanan test, bu sorunu da test etmek için çalışır.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktası sildikten sonra hata ayıklamaya yeniden başlarken kesme noktasıyla çalışmaya devam ediyorum

Hata ayıklama sırasında bir kesme noktası sildikten sonra hata ayıklamaya yeniden başlayabilirsiniz. Bu kesme noktalarına isabet etmeyi durdurmak için kesme noktası örneklerinin tüm kesme noktaları penceresinden **kaldırıldıklarından emin** olun.
