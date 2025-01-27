---
title: Hata ayıklayıcıda kesme noktaları sorunlarını giderme | Microsoft Docs
description: Kesme noktası devre dışıysa veya ayarlanamayacak boş bir daire olarak görüntülenir. Kesme noktaları ayarlanırken oluşabilecek sorunlar hakkında buraya bakın.
ms.date: 01/10/2022
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.custom: devdivchpfy22
ms.openlocfilehash: dc2f7ccd780c8675a7812d370f6dce9ff744eaa8
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805265"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıda kesme noktaları sorunlarını giderme

## <a name="breakpoint-warnings"></a>Kesme noktası uyarıları

Hata ayıklarken, kesme noktasında iki olası görsel durum vardır:

* Hata ayıklayıcı hedef işlemde başarıyla bir kesme noktası ayarlandıysa, düz kırmızı bir daire.
* Boş (beyaz doldurulmuş) Daire, kesme noktası devre dışı bırakılır ya da kesme noktası ayarlanmaya çalışılırken uyarı oluşmuştur.

Farkı öğrenmek için kesme noktasının üzerine gelin ve bir uyarı olup olmadığını görün. Aşağıdaki iki bölümde belirgin uyarılar ve bunların nasıl düzeltileceğini açıklamaktadır.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Bu belge için sembol yüklenmedi"

**modüller** penceresine gidin (**hata ayıklama**  >  **Windows**  >  **modülleri**) ve modülünüzün yüklenip yüklenmediğini denetleyin.

* Modülünüz yüklüyse, simgelerin yüklenip yüklenmediğini görmek için **sembol durumu** sütununu kontrol edin.
  * Semboller yüklü değilse, sorunu tanılamak için sembol durumunu kontrol edin. **Modüller** penceresindeki bir modülün bağlam menüsünde **sembol yükleme bilgileri...** ' ni seçin ve hata ayıklayıcı 'nın sembolleri denemek ve yüklemek için baktığı yeri görüntüleyin. Sembolleri yükleme hakkında daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Semboller yüklüyse PDB, kaynak dosyalarınız hakkında bilgi içermez. Olası birkaç neden şunlardır:
    * Kaynak dosyalarınız son zamanlarda eklendiyse, modülün güncel sürümünün yüklenmekte olduğunu onaylayın.
    * **/Pdbçıkarıldı** bağlayıcı seçeneğini kullanarak, pdb 'leri oluşturulabilir. Pdb 'leri, kaynak dosya bilgilerini içermiyor. Bir tam PDB ile çalıştığınızı ve bu şekilde kesilmiş bir PDB Not kullandığınızı onaylayın.
    * PDB dosyası kısmen bozuk. Sorunu çözmeye çalışmak için dosyayı silin ve modülün temiz bir derlemesini çalıştırın.

* Modülünüzün yüklü olmaması durumunda nedenini bulmak için aşağıdakileri denetleyin:
  * Doğru işlemde hata ayıkladığınızı onaylayın.
  * Doğru kodda hata ayıkladığınızı görmek için denetleyin. hata ayıklayıcının, **işlem** penceresinde hata ayıklamak için ne tür bir kod ile yapılandırıldığını öğrenebilirsiniz (**hata ayıklama**  >  **Windows**  >  **işlemlerinde**). Örneğin, C# kodunda hata ayıklamaya çalışıyorsanız, hata ayıklayıcının .NET 'in uygun türü ve sürümü (örneğin, yönetilen (v4) ile yönetilen ( \* v2 \* /v3 \* ) Ile yönetilen (CoreCLR)) için yapılandırıldığını doğrulayın.

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… geçerli kaynak kodu, yerleşik sürümünden farklı... "

Bir kaynak dosya değiştiyse ve kaynak artık hata ayıklamada olduğunuz kodla eşleşmez, hata ayıklayıcı varsayılan olarak kodda kesme noktaları ayarlar. Normalde, bu sorun bir kaynak dosya değiştirildiğinde, ancak kaynak kodu yeniden oluşturulmadığında oluşur. Bu sorunu onarmak için projeyi yeniden derleyin. Yapı sistemi projenin zaten güncel olup olmadığını düşündüğü halde, proje sistemini yeniden oluşturmaya zorlayabilirsiniz. Kaynak dosyayı tekrar kaydederek ya da derlemeden önce derleme çıkışını kaldırarak projeyi yeniden derleyin.

Nadir senaryolarda, eşleşen kaynak kodu olmadan hata ayıklaması yapmak isteyebilirsiniz. Eşleşen kaynak kodu olmadan hata ayıklama, kafa karıştırıcı bir hata ayıklama deneyimine yol açabilir, bu nedenle devam etmek istediğinize emin olun.

Bu güvenlik denetimlerini devre dışı bırakmak için seçeneklerden birini izleyin:

* Tek bir kesme noktasını değiştirmek için düzenleyicide kesme noktası simgesinin üzerine gelin ve ayarlar (dişli) simgesini seçin. Düzenleyiciye bir göz atma penceresi eklenir. Göz atma penceresinin üst kısmında, kesme noktasının konumunu gösteren bir köprü bulunur. Kesme noktası konumunun değiştirilmesine izin vermek için köprüyü seçin ve **kaynak kodun orijinalden farklı olmasını** sağlar.
* tüm kesme noktaları için bu ayarı değiştirmek üzere **hata ayıklama**  >  **seçenekleri ve Ayarlar** gidin. **Hata ayıklama/genel** sayfasında, **özgün sürümle tam olarak eşleşen kaynak dosyalarını gerektir** seçeneğini temizleyin. Hata ayıklamayı bitirdiğinizde bu seçeneği yeniden etkinleştirdiğinizden emin olun.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Kesme noktası başarıyla ayarlandı (uyarı yok), ancak isabet etmedi

Bu bölüm, hata ayıklayıcı herhangi bir uyarı görüntülemediğinde oluşan sorunları gidermek için bilgiler sağlar. kesme noktası etkin bir şekilde hata ayıklaırken düz kırmızı bir daire, ancak kesme noktası isabet etmemektedir.

Şunları denetlemeniz gereken birkaç nokta vardır:

1. Kodunuz birden fazla işlemde veya birden çok bilgisayarda çalışıyorsa, doğru işlem veya bilgisayarda hata ayıkladığınızdan emin olun.
2. Kodunuzun çalıştığını doğrulayın. Kodunuzun çalıştığını test etmek için, `System.Diagnostics.Debugger.Break` kesme noktasını ayarlamaya çalıştığınız kod satırına (C#/vb) veya `__debugbreak` (C++) çağrısı ekleyin ve ardından projenizi yeniden derleyin.
3. İyileştirilmiş kodda hata ayıklaması yapıyorsanız, kesme noktasının ayarlandığı işlevin başka bir işleve satır içine alınmayacak olduğundan emin olun. `Debugger.Break`Önceki denetim bölümünde açıklanan test, bu sorunu da test etmek için çalışabilir.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktasını sildim, ancak hata ayıklamayı yeniden başlattığımda bu kez vurmaya devam ediyorum

Hata ayıklarken bir kesme noktasını sildiyseniz, hata ayıklamayı bir sonraki başlatmanızda kesme noktasına bir daha basabilirsiniz. Bu kesme noktasına vurmak **için kesme noktası penceresinin tüm** örneklerinin kaldırıldığından emin olun.
