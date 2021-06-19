---
title: Hata ayıklayıcıda kesme noktaları sorunlarını giderme | Microsoft Docs
description: Kesme noktası devre dışıysa veya ayarlanmamışsa, boş bir daire olarak görüntülenir. Kesme noktaları ayarlanırken oluşabilecek sorunlar hakkında buraya bakın.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0801a687529b5e0f8cdf34030460f0b5fe45bc91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386390"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme

## <a name="breakpoint-warnings"></a>Kesme noktası uyarıları

Hata ayıklarken, kesme noktasında iki olası görsel durum vardır: düz kırmızı daire ve boş (beyaz doldurulmuş) Daire. Hata ayıklayıcı hedef işlemde başarıyla bir kesme noktası ayarlayabiliyor ise, düz bir kırmızı daire kalır. Kesme noktası boş bir daire ise kesme noktası devre dışı bırakılır ya da kesme noktası ayarlanmaya çalışılırken uyarı oluşmuştur. Farkı öğrenmek için kesme noktasının üzerine gelin ve bir uyarı olup olmadığını görün.

Aşağıdaki iki bölümde belirgin uyarılar ve bunların nasıl düzeltileceğini açıklamaktadır.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Bu belge için sembol yüklenmedi"

**Modüller** penceresine gidin (Windows modüllerine **hata ayıklayın**  >    >  ) ve modülünüzün yüklenip yüklenmediğini denetleyin.
* Modülünüz yüklüyse, simgelerin yüklenip yüklenmediğini görmek için **sembol durumu** sütununu kontrol edin.
  * Semboller yüklü değilse, sorunu tanılamak için sembol durumunu kontrol edin. **Modüller** penceresindeki bir modülün bağlam menüsünde **sembol yükleme bilgileri...** ' ya tıklayarak hata ayıklayıcının sembolleri denemek ve yüklemek için baktığı yeri görüntüleyin. Sembolleri yükleme hakkında daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Semboller yüklüyse PDB, kaynak dosyalarınız hakkında bilgi içermez. Bunlar olası nedenleri şunlardır:
    * Kaynak dosyalarınız son zamanlarda eklendiyse, modülün güncel sürümünün yüklenmekte olduğunu onaylayın.
    * **/Pdbçıkarıldı** bağlayıcı seçeneği kullanılarak, pdb 'leri oluşturulabilir. Pdb 'leri, kaynak dosya bilgilerini içermez. Bir tam PDB ile çalıştığınızı ve bir kesilmiş PDB değil olduğunu onaylayın.
    * PDB dosyası kısmen bozuk. Dosyayı silin ve sorunu çözmeye çalışmak için modülün temiz bir derlemesini gerçekleştirin.

* Modülünüzün yüklü olmaması durumunda nedenini bulmak için aşağıdakileri denetleyin:
  * Doğru işlemde hata ayıklatığınızdan emin olun.
  * Doğru kod türünde hata ayıklamanın olup olmadığını kontrol edin. Hata ayıklayıcının, **işlem** penceresinde hata ayıklamak için ne tür bir kod ile yapılandırıldığını öğrenebilirsiniz (Windows işlemlerinde **Hata Ayıkla**  >    >  ). Örneğin, C# kodunda hata ayıklamaya çalışıyorsanız, hata ayıklayıcının .NET 'in uygun türü ve sürümü (örneğin, yönetilen (v4) ile yönetilen ( \* v2 \* /v3 \* ) Ile yönetilen (CoreCLR)) için yapılandırıldığını doğrulayın.

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… geçerli kaynak kodu, yerleşik sürümünden farklı... "

Bir kaynak dosya değiştiyse ve kaynak artık hata ayıkladığınız kodla eşleşmez, hata ayıklayıcı varsayılan olarak kodda kesme noktaları ayarlanmayacaktır. Normalde, bu sorun bir kaynak dosya değiştirildiğinde, ancak kaynak kodu yeniden oluşturulmadığında oluşur. Bu sorunu onarmak için projeyi yeniden derleyin. Yapı sistemi projenin zaten güncel olup olmadığını düşündüğü halde, kaynak dosyayı yeniden kaydederek ya da derlemeden önce projenin derleme çıkışını kaldırarak proje sistemini yeniden oluşturmaya zorlayabilirsiniz.

Nadir senaryolarda, eşleşen kaynak kodu olmadan hata ayıklaması yapmak isteyebilirsiniz. Eşleşen kaynak kodu olmadan hata ayıklama, kafa karıştırıcı bir hata ayıklama deneyimine yol açabilir, bu nedenle bunun nasıl devam etmek istediğinize emin olun.

Bu güvenlik denetimlerini devre dışı bırakmak için aşağıdakilerden birini yapın:
* Tek bir kesme noktasını değiştirmek için, düzenleyicide kesme noktası simgesinin üzerine gelin ve ayarlar (dişli) simgesine tıklayın. Düzenleyiciye bir göz atma penceresi eklenir. Göz atma penceresinin üst kısmında, kesme noktasının konumunu gösteren bir köprü bulunur. Kesme noktası konumunun değiştirilmesine izin vermek için köprüye tıklayın ve **kaynak kodun orijinalden farklı olmasını** sağlar.
* Tüm kesme noktaları için bu ayarı değiştirmek üzere **hata ayıklama**  >  **seçenekleri ve ayarlar**'a gidin. **Hata ayıklama/genel** sayfasında, **özgün sürümle tam olarak eşleşen kaynak dosyalarını gerektir** seçeneğini temizleyin. Hata ayıklamayı bitirdiğinizde bu seçeneği yeniden etkinleştirdiğinizden emin olun.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Kesme noktası başarıyla ayarlandı (uyarı yok), ancak isabet etmedi

Bu bölüm, hata ayıklayıcı herhangi bir uyarı görüntülemediğinde oluşan sorunları gidermek için bilgiler sağlar. kesme noktası etkin bir şekilde hata ayıklaırken düz kırmızı bir daire, ancak kesme noktası isabet etmemektedir.

Şunları denetlemeniz gereken birkaç nokta vardır:
1. Kodunuz birden fazla işlemde veya birden çok bilgisayarda çalışıyorsa, doğru işlem veya bilgisayarda hata ayıkladığınızdan emin olun.
2. Kodunuzun çalıştığını doğrulayın. Kodunuzun çalıştığını test etmek için, `System.Diagnostics.Debugger.Break` kesme noktasını ayarlamaya çalıştığınız kod satırına (C#/vb) veya `__debugbreak` (C++) çağrısı ekleyin ve ardından projenizi yeniden derleyin.
3. İyileştirilmiş kodda hata ayıklaması yapıyorsanız, kesme noktasının ayarlandığı işlevin başka bir işleve satır içine alınmayacak olduğundan emin olun. `Debugger.Break`Önceki denetim bölümünde açıklanan test, bu sorunu da test etmek için çalışabilir.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktasını sildim, ancak hata ayıklamayı yeniden başlattığımda bu kez vurmaya devam ediyorum

Hata ayıklarken bir kesme noktasını sildiyseniz, hata ayıklamayı bir sonraki başlatmanızda kesme noktasına bir daha basabilirsiniz. Bu kesme noktasına vurmak **için kesme noktası penceresinin tüm** örneklerinin kaldırıldığından emin olun.
