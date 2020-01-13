---
title: ClickOnce dağıtımlarında belirli hataların sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81bb9bcecf37d2ed3fca29a4edc57738732de1a5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917273"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>ClickOnce Dağıtımları İçinde Belirli Hataları Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması dağıtırken oluşabilecek aşağıdaki yaygın hataları listeler ve her bir sorunu çözmek için gereken adımları sağlar.  
  
## <a name="general-errors"></a>Genel hatalar  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Internet Explorer 'da bir. Application dosyası, hiçbir şey veya XML işleme bulmaya çalıştığınızda ya da bir Çalıştır veya farklı Kaydet iletişim kutusu alırsanız  
 Bu hata, büyük olasılıkla içerik türlerinin (MIME türleri olarak da bilinir) sunucu veya istemciye doğru kaydedilmemesinin nedeni olabilir.  
  
 İlk olarak, sunucunun. Application uzantısını "application/x-MS-Application" içerik türüyle ilişkilendirmek için yapılandırıldığından emin olun.  
  
 Sunucu doğru yapılandırılmışsa [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] bilgisayarınızda yüklü olduğundan emin olun. [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] yüklüyse ve bu sorunu görmeye devam ediyorsanız, içerik türünü istemciye yeniden kaydetmek için [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] kaldırıp yeniden yüklemeyi deneyin.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Hata iletisi şöyle, "uygulama alınamıyor. Dağıtımda eksik dosyalar "veya" uygulama indirme işlemi kesildi, ağ hatalarını kontrol edin ve daha sonra yeniden deneyin "  
 Bu ileti, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimleri tarafından başvurulan bir veya daha fazla dosyanın indirilebileceğini gösterir. Bu hatayı hata ayıklamanın en kolay yolu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] indirmediği belirten URL 'YI indirmeye çalışır. Olası bazı nedenler şunlardır:  
  
- Günlük dosyası "(403) yasak" veya "(404) bulunamadı" diyorsa, Web sunucusunun bu dosyanın indirilmesini engellememek için yapılandırıldığını doğrulayın. Daha fazla bilgi için bkz. [ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
- . Config dosyası sunucu tarafından engelleniyorsa, bu konunun ilerleyen kısımlarında yer alan ". config dosyasına sahip bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yüklemeye çalıştığınızda karşıdan yükleme hatası" bölümüne bakın.  
  
- Dağıtım bildirimindeki `deploymentProvider` URL 'SI etkinleştirme için kullanılan URL 'den farklı bir konuma işaret ettiğinden bunun oluşup oluşmadığını belirleme.  
  
- Tüm dosyaların sunucuda bulunduğundan emin olun; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] günlüğü size hangi dosyanın bulunamadığını söylemelidir.  
  
- Ağ bağlantısı sorunları olup olmadığını öğrenin; Bu iletiyi, istemci bilgisayarınız indirme sırasında çevrimdışı olursa alırsınız.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>. Config dosyasına sahip bir ClickOnce uygulaması yüklemeye çalıştığınızda indirme hatası  
 Varsayılan olarak, Visual Basic Windows tabanlı bir uygulama bir App. config dosyası içerir. Bir Kullanıcı Windows Server 2003 kullanan bir Web sunucusundan yüklemeye çalıştığında, işletim sistemi güvenlik nedenleriyle. config dosyalarının yüklenmesini engellediği için bir sorun olacaktır. . Config dosyasının yüklenmesini etkinleştirmek için **Yayımlama seçenekleri** iletişim kutusunda **". deploy" dosya uzantısını kullan** ' a tıklayın.  
  
 Ayrıca,. Application,. manifest ve. deploy dosyaları için uygun içerik türlerini (MIME türleri olarak da bilinir) ayarlamanız gerekir. Daha fazla bilgi için Web sunucusu belgelerinize bakın.  
  
 Daha fazla bilgi için, bkz. "Windows Server 2003: kilitlenmiş Içerik türleri"; [sunucu ve ClickOnce dağıtımlarında Istemci Yapılandırma sorunları](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Hata iletisi: "uygulama hatalı biçimlendirildi;" "XML imzası geçersiz" içeren günlük dosyası  
 Bildirim dosyasını güncelleştirdiğinizden ve yeniden imzaladığınızdan emin olun. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak uygulamanızı yeniden yayımlayın veya uygulamayı yeniden imzalamak için Mage kullanın.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Uygulamanızı sunucuda güncelleştirdiniz, ancak istemci güncelleştirmeyi indirmiyor  
 Bu sorun aşağıdaki görevlerden biri tamamlanarak çözülebilir:  
  
- Dağıtım bildiriminde `deploymentProvider` URL 'sini inceleyin. `deploymentProvider` işaret eden aynı konumdaki bitleri güncelleştirdiğinizden emin olun.  
  
- Dağıtım bildiriminde güncelleştirme aralığını doğrulayın. Bu Aralık, altı saatte bir bir zaman gibi düzenli bir aralığa ayarlanırsa, bu Aralık geçene kadar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] güncelleştirme taramayacaktır. Uygulamanın her başlayışında, bir güncelleştirmeyi taramak için bildirimi değiştirebilirsiniz. Güncelleştirme aralığının değiştirilmesi, güncelleştirmelerin yüklenmekte olduğunu doğrulamak için geliştirme zamanı sırasında kullanışlı bir seçenektir, ancak uygulama etkinleştirmeyi yavaşlatır.  
  
- Başlat menüsünde uygulamayı yeniden başlatmayı deneyin. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arka planda güncelleştirmeyi algılamış olabilir, ancak bir sonraki etkinleştirmeye bitleri yüklemenizi ister.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Güncelleştirme sırasında şu günlük girişine sahip bir hata alırsınız: "dağıtımdaki başvuru, uygulama bildiriminde tanımlanan kimlikle eşleşmiyor"  
 Bu hata, dağıtım ve uygulama bildirimlerini el ile düzenlediğiniz ve bir bildirimdeki derlemenin kimliğinin diğer ile eşitlenmemiş hale gelmesine neden olmuş olabileceğinden meydana gelebilir. Bir derlemenin kimliği ad, sürüm, kültür ve ortak anahtar belirtecinden oluşur. Bildirimlerinizde kimlik açıklamalarını inceleyin ve farkları düzeltin.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Yerel diskten veya CD-ROM ' d a n ilk kez etkinleştirme başarılı olur, ancak başlangıç menüsünden sonraki etkinleştirme başarılı olmaz  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], uygulama için güncelleştirmeleri almak üzere dağıtım sağlayıcısı URL 'sini kullanır. URL 'nin işaret ettiği konumun doğru olduğunu doğrulayın.  
  
#### <a name="error-cannot-start-the-application"></a>Hata: "uygulama başlatılamıyor"  
 Bu hata iletisi genellikle bu uygulamayı [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deposuna yüklerken bir sorun olduğunu gösterir. Uygulamada bir hata ya da depo bozulmuş. Günlük dosyası sizi hatanın nerede oluştuğunu söyleyebilir.  
  
 Şunları yapmalısınız:  
  
- Dağıtım bildiriminin kimliğinin, uygulama bildiriminin kimliğinin ve ana uygulama EXE kimliğinin tümünün benzersiz olduğunu doğrulayın.  
  
- Dosya yollarınızın 100 karakterden uzun olmadığından emin olun. Uygulamanız çok uzun dosya yolları içeriyorsa, depolayabileceği en fazla yol üzerindeki sınırlamaları aşabilirsiniz. Yolları kısaltmayı ve yeniden yüklemeyi deneyin.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Uygulama yapılandırma dosyasındaki PrivatePath ayarları kabul edilmez  
 PrivatePath (Fusion yoklama yolları) kullanmak için, uygulamanın tam güven izni istemesi gerekir. Uygulama bildirimini tam güven isteyecek şekilde değiştirmeyi deneyin ve sonra yeniden deneyin.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Kaldırma sırasında bir ileti görünür, "uygulama kaldırılamadı" iletisini alıyorum  
 Bu ileti genellikle uygulamanın zaten kaldırıldığını veya deponun bozulduğunu gösterir. **Tamam**' a tıkladıktan sonra **Program Ekle/Kaldır** girdisi kaldırılır.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Yükleme sırasında, platform bağımlılıklarının yüklenmediğini belirten bir ileti görüntülenir  
 Uygulamanın çalışması için gerekli olan GAC 'de (genel derleme önbelleği) bir önkoşulu eksik.  
  
## <a name="publishing-with-visual-studio"></a>Visual Studio ile yayımlama  
  
#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio 'da yayımlama başarısız oluyor  
 Hedeflediğiniz sunucuda yayımlama hakkına sahip olduğunuzdan emin olun. Örneğin, bir Terminal sunucusu bilgisayarında yönetici olarak değil, sıradan bir kullanıcı olarak oturum açtıysanız, muhtemelen yerel Web sunucusuna yayımlamak için gerekli haklara sahip olmayacaktır.  
  
 Bir URL ile yayınlıyorsanız, hedef bilgisayarda FrontPage Server Extensions 'ın etkinleştirildiğinden emin olun.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Hata Iletisi: '\<site > ' Web sitesi oluşturulamıyor. FrontPage Server uzantılarıyla iletişim kurmak için bileşenler yüklü değil.  
 Yayımlamakta olduğunuz makinede Microsoft Visual Studio Web yazma bileşeninin yüklü olduğundan emin olun. Express kullanıcıları için bu bileşen varsayılan olarak yüklenmez.  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Hata iletisi: dosya bulunamadı. ' Microsoft.Windows.Common-denetimleri, sürüm= 6.0.0.0, kültür =\*, PublicKeyToken 6595b64144ccf1df, ProcessorArchitecture =\*, türü= win32'  
 Bu hata iletisi, görsel stiller etkinken bir WPF uygulaması yayımlamaya çalıştığınızda görüntülenir. Bu sorunu çözmek için bkz. [nasıl yapılır: görsel STILLERLE WPF uygulaması yayımlama etkin](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Mage kullanma  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sertifika deponuzda bir sertifikayla oturum açmaya çalıştınız ve alınan boş ileti kutusu  
 **İmzalama** iletişim kutusunda şunları yapmanız gerekir:  
  
- **Depolanan sertifikayla imzala**' yı seçin ve  
  
- Listeden bir sertifika seçin; ilk sertifika varsayılan seçim değildir.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>"Oturum açma" düğmesine tıklamak özel duruma neden olur  
 Bu sorun bilinen bir hatadır. Tüm [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimlerinin imzalanması gerekir. İmzalama seçeneklerinden birini seçmeniz yeterlidir ve ardından **Tamam**' a tıklayın.  
  
## <a name="additional-errors"></a>Ek hatalar  
 Aşağıdaki tabloda, Kullanıcı [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir uygulama yüklediğinde istemci-bilgisayar kullanıcısının alabileceği bazı yaygın hata iletileri gösterilmektedir. Her hata iletisi, hatanın en olası nedeni açıklamasının yanında listelenir.  
  
|Hata iletisi|Açıklama|  
|-------------------|-----------------|  
|Uygulama başlatılamıyor. Uygulama yayımcısına başvurun.<br /><br /> Uygulama başlatılamıyor. Yardım almak için uygulama satıcısına başvurun.|Bunlar, uygulama başlatılmadan oluşan genel hata iletilerdir ve başka bir özel neden bulunamamalıdır. Bu, genellikle uygulamanın bozulmuş olduğu veya [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deposunun bozuk olduğu anlamına gelir.|  
|Devam edilemiyor. Uygulama Hatalı biçimli. Yardım almak için uygulama yayımcısına başvurun.<br /><br /> Uygulama doğrulaması başarılı olmadı. Devam edilemiyor.<br /><br /> Uygulama dosyaları alınamıyor. Dağıtımdaki dosyalar bozuk.|Dağıtımdaki bildirim dosyalarından biri sözdizimsel olarak geçerli değil veya karşılık gelen dosyayla mutabık kılınabilecek bir karma içeriyor. Bu hata, bir derleme içine gömülü bildirimin bozuk olduğunu da gösterebilir. Dağıtımınızı yeniden oluşturun ve uygulamanızı yeniden derleyin ya da bildirimlerinizde el ile hataları bulup onarın.|  
|Uygulama alınamıyor. Kimlik doğrulama hatası.<br /><br /> Uygulama yüklemesi başarılı olmadı. Sunucudaki uygulama dosyaları bulunamıyor. Yardım için uygulama yayımcısına veya yöneticinize başvurun.|Dağıtımdaki bir veya daha fazla dosya, bunlara erişim izniniz olmadığından indirilemiyor. Bunun nedeni, bir Web sunucusu tarafından döndürülen 403 yasaklanmış bir hata olabilir. bu durum, dağıtımınızdaki dosyalardan biri Web sunucusunun korumalı bir dosya olarak kabul eden bir uzantıyla biterse meydana gelebilir. Ayrıca, bir veya daha fazla uygulama dosyasını içeren bir dizin, erişim için bir Kullanıcı adı ve parola gerektirebilir.|  
|Uygulama indirilemiyor. Uygulamada gerekli dosyalar eksik. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Uygulama bildiriminde listelenen bir veya daha fazla dosya sunucuda bulunamıyor. Tüm dağıtımın bağımlı dosyalarını karşıya yüklediğinizi doğrulayın ve yeniden deneyin.|  
|Uygulama indirmesi başarılı olmadı. Ağ bağlantınızı denetleyin veya sistem yöneticinize veya ağ hizmeti sağlayıcısına başvurun.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sunucuya ağ bağlantısı kuramıyor. Sunucunun kullanılabilirliğini ve ağınızın durumunu inceleyin.|  
|URLDownloadToCacheFile, HRESULT '\<Number > ' ile başarısız oldu. '\<File > ' indirilmeye çalışılırken bir hata oluştu.|Bir Kullanıcı, dağıtım hedef bilgisayarında Internet Explorer Gelişmiş Güvenlik seçeneğini "güvenli ve güvenli olmayan mod arasında değişiklik yaptıysanız uyar" olarak ayarlandıysa ve yüklenmekte olan ClickOnce uygulamasının kurulum URL 'SI güvenli bir sitede güvenli olmayan bir siteye yönlendiriliyorsa (veya tersi), Internet Explorer uyarısı bunu kestiğinden yükleme başarısız olur.<br /><br /> Bunu çözmek için aşağıdakilerden birini yapabilirsiniz:<br /><br /> -Güvenlik seçeneğini temizleyin.<br />-Kurulum URL 'sinin güvenlik modlarını değiştiren bir şekilde yeniden yönlendirilmediğinden emin olun.<br />-Yeniden yönlendirmeyi tamamen kaldırın ve gerçek kurulum URL 'sini işaret edin.|  
|Sabit diske yazılırken bir hata oluştu. Diskte yeterli alan yok olabilir. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Bu, uygulamayı depolamak için yeterli disk alanı olduğunu gösterebilir, ancak uygulama dosyalarını sürücüye kaydetmeye çalışırken daha genel bir g/ç hatası da belirtebilir.|  
|Uygulama başlatılamıyor. Diskte yeterli kullanılabilir alan yok.|Sabit disk dolu. Alanı temizleyin ve uygulamayı yeniden çalıştırmayı deneyin.|  
|Çok fazla dağıtılan etkinleştirme aynı anda yüklenmeye çalışıyor.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], aynı anda başlayabilirler farklı uygulamalar sayısını sınırlar. Bu, yerel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] hizmetine karşı hizmet reddi saldırılarına karşı kötü amaçlı saldırılara karşı korumaya yardımcı olmak büyük ölçüde önemlidir; aynı uygulamayı art arda baştan çalıştırmayı deneyen kullanıcılar, yalnızca uygulamanın tek bir örneğiyle birlikte sona kalır.|  
|Kısayollar ağ üzerinden etkinleştirilemez.|Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamasının kısayolları yalnızca yerel sabit diskte başlatılabilir. Uzak bir sunucudaki kısayol dosyasına işaret eden bir URL açılarak başlatılamaz.|  
|Uygulama kısmi güvende çevrimiçi çalıştırılamayacak kadar büyük. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun.|Kısmi güvende çalışan bir uygulama, varsayılan olarak 250 MB olan çevrimiçi uygulama kotasının boyutunun yarısından daha büyük olamaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtım](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Dağıtım Sorunlarını Giderme](../deployment/troubleshooting-clickonce-deployments.md)
