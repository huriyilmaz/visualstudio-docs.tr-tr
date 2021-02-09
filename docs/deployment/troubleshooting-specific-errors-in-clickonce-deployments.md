---
title: Sorun giderme hataları (ClickOnce dağıtımları)
description: Bu makalede, bir ClickOnce uygulaması dağıttığınızda oluşabilecek yaygın hatalar açıklanmakta ve her bir sorunu çözmek için adımlar sağlanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4697aa4869535d63c522ae25c978dd89bfe51697
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876179"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>ClickOnce dağıtımları içinde belirli hataları giderme
Bu makalede, bir uygulamayı dağıtırken oluşabilecek aşağıdaki yaygın hatalar listelenir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve her bir sorunu çözmek için adımlar sağlanır.

## <a name="general-errors"></a>Genel hatalar

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Bir uygulama dosyasını bulmaya çalıştığınızda, hiçbir şey gerçekleşmez veya Internet Explorer 'da XML oluşturma veya farklı Kaydet iletişim kutusu alıyorsunuz
 Bu hata, büyük olasılıkla içerik türlerinin (MIME türleri olarak da bilinir) sunucu veya istemciye doğru kaydedilmemesinin nedeni olabilir.

 İlk olarak, sunucunun *. Application* uzantısını "application/x-MS-Application" içerik türüyle ilişkilendirmek için yapılandırıldığından emin olun.

 Sunucu doğru yapılandırılmışsa, .NET Framework 2,0 ' in bilgisayarınızda yüklü olduğundan emin olun. 2,0 .NET Framework yüklüyse ve bu sorunu görmeye devam ediyorsanız, içerik türünü istemciye yeniden kaydetmek için .NET Framework 2,0 ' yi kaldırıp yeniden yüklemeyi deneyin.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Hata iletisi şöyle, "uygulama alınamıyor. Dağıtımda eksik dosyalar "veya" uygulama indirme işlemi kesildi, ağ hatalarını kontrol edin ve daha sonra yeniden deneyin "
 Bu ileti, bildirimlerin başvurduğu bir veya daha fazla dosyanın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indirilebileceğini gösterir. Bu hatayı ayıklamanın en kolay yolu, indirmediği belirten URL 'YI indirmeye çalışacaktır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Olası bazı nedenler şunlardır:

- Günlük dosyası "(403) yasak" veya "(404) bulunamadı" diyorsa, Web sunucusunun bu dosyanın indirilmesini engellememek için yapılandırıldığını doğrulayın. Daha fazla bilgi için bkz. [ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

- *. Config* dosyası sunucu tarafından engelleniyorsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu makalenin sonraki kısımlarında yer alan ". config dosyası olan bir uygulamayı yüklemeye çalıştığınızda karşıdan yükleme hatası" bölümüne bakın.

- `deploymentProvider`Dağıtım bildirimindeki URL, etkinleştirme için kullanılan URL 'den farklı bir konuma işaret ettiğinden, bu hatanın oluşup oluşmadığını belirleme.

- Tüm dosyaların sunucuda bulunduğundan emin olun; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] günlük, hangi dosyanın bulunamadığını anlatmalıdır.

- Ağ bağlantısı sorunları olup olmadığını öğrenin; Bu iletiyi, istemci bilgisayarınız indirme sırasında çevrimdışı olursa alırsınız.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>. Config dosyasına sahip bir ClickOnce uygulaması yüklemeye çalıştığınızda indirme hatası
 Varsayılan olarak, Visual Basic Windows tabanlı bir uygulama App.config bir dosya içerir. Bir Kullanıcı Windows Server 2003 kullanan bir Web sunucusundan yüklemeye çalıştığında, işletim sistemi güvenlik nedenleriyle *. config* dosyalarının yüklenmesini engellediği için bir sorun olacaktır. *. Config* dosyasının yüklenmesini etkinleştirmek Için **Yayımlama seçenekleri** iletişim kutusunda **". deploy" dosya uzantısını kullan** ' a tıklayın.

 Ayrıca,. Application,. manifest ve. deploy dosyaları için uygun içerik türlerini (MIME türleri olarak da bilinir) ayarlamanız gerekir. Daha fazla bilgi için Web sunucusu belgelerinize bakın.

 Daha fazla bilgi için, bkz. "Windows Server 2003: kilitlenmiş Içerik türleri"; [sunucu ve ClickOnce dağıtımlarında istemci yapılandırma sorunları](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Hata iletisi: "uygulama hatalı biçimlendirildi;" "XML imzası geçersiz" içeren günlük dosyası
 Bildirim dosyasını güncelleştirdiğinizden ve yeniden imzaladığınızdan emin olun. Kullanarak uygulamanızı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yeniden yayımlayın veya uygulamayı yeniden imzalamak Için Mage 'ı kullanın.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Uygulamanızı sunucuda güncelleştirdiniz, ancak istemci güncelleştirmeyi indirmiyor
 Bu sorun aşağıdaki görevlerden biri tamamlanarak çözülebilir:

- `deploymentProvider`Dağıtım bildiriminde URL 'yi inceleyin. BITS 'yi işaret eden aynı konumda güncelleştirdiğinizden emin olun `deploymentProvider` .

- Dağıtım bildiriminde güncelleştirme aralığını doğrulayın. Bu Aralık, altı saatte bir bir zaman gibi düzenli bir aralığa ayarlanırsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu Aralık geçene kadar bir güncelleştirmeyi taramayacaktır. Uygulamanın her başlayışında, bir güncelleştirmeyi taramak için bildirimi değiştirebilirsiniz. Güncelleştirme aralığının değiştirilmesi, güncelleştirmelerin yüklenmekte olduğunu doğrulamak için geliştirme zamanı sırasında kullanışlı bir seçenektir, ancak uygulama etkinleştirmeyi yavaşlatır.

- Başlat menüsünde uygulamayı yeniden başlatmayı deneyin. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , arka planda güncelleştirmeyi algılamış olabilir, ancak bir sonraki etkinleştirmeye bitleri yüklemenizi ister.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Güncelleştirme sırasında şu günlük girişine sahip bir hata alırsınız: "dağıtımdaki başvuru, uygulama bildiriminde tanımlanan kimlikle eşleşmiyor"
 Bu hata, dağıtım ve uygulama bildirimlerini el ile düzenlediğiniz ve bir bildirimdeki derlemenin kimliğinin diğer ile eşitlenmemiş hale gelmesine neden olmuş olabileceğinden meydana gelebilir. Bir derlemenin kimliği ad, sürüm, kültür ve ortak anahtar belirtecinden oluşur. Bildirimlerinizde kimlik açıklamalarını inceleyin ve farkları düzeltin.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Yerel diskten veya CD-ROM ' d a n ilk kez etkinleştirme başarılı olur, ancak başlangıç menüsünden sonraki etkinleştirme başarılı olmaz
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama için güncelleştirmeleri almak üzere dağıtım sağlayıcısı URL 'sini kullanır. URL 'nin işaret ettiği konumun doğru olduğunu doğrulayın.

#### <a name="error-cannot-start-the-application"></a>Hata: "uygulama başlatılamıyor"
 Bu hata iletisi genellikle bu uygulamayı depoya yüklerken bir sorun olduğunu gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Uygulamada bir hata ya da depo bozulmuş. Günlük dosyası sizi hatanın nerede oluştuğunu söyleyebilir.

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

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Hata iletisi: ' ' Web sitesi oluşturulamıyor \<site> . FrontPage Server uzantılarıyla iletişim kurmak için bileşenler yüklü değil.
 Yayımlamakta olduğunuz makinede Microsoft Visual Studio Web yazma bileşeninin yüklü olduğundan emin olun. Express kullanıcıları için bu bileşen varsayılan olarak yüklenmez. Daha fazla bilgi için bkz. [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Hata iletisi: ' Microsoft. Windows. Common-Controls, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = Win32 ' dosyası bulunamadı
 Bu hata iletisi, görsel stiller etkinken bir WPF uygulaması yayımlamaya çalıştığınızda görüntülenir. Bu sorunu çözmek için bkz. [nasıl yapılır: görsel STILLERLE WPF uygulaması yayımlama etkin](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).

## <a name="using-mage"></a>Mage kullanma

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sertifika deponuzda bir sertifikayla oturum açmaya çalıştınız ve alınan boş ileti kutusu
 **İmzalama** iletişim kutusunda şunları yapmanız gerekir:

- **Depolanan sertifikayla imzala**' yı seçin ve

- Listeden bir sertifika seçin; ilk sertifika varsayılan seçim değildir.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>"Oturum açma" düğmesine tıklamak özel duruma neden olur
 Bu sorun bilinen bir hatadır. Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimlerin imzalanması gerekir. İmzalama seçeneklerinden birini seçmeniz yeterlidir ve ardından **Tamam**' a tıklayın.

## <a name="additional-errors"></a>Ek hatalar
 Aşağıdaki tabloda, Kullanıcı bir uygulama yüklediğinde istemci-bilgisayar kullanıcısının alabileceği bazı yaygın hata iletileri gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Her hata iletisi, hatanın en olası nedeni açıklamasının yanında listelenir.

| Hata iletisi | Description |
| - | - |
| Uygulama başlatılamıyor. Uygulama yayımcısına başvurun.<br /><br /> Uygulama başlatılamıyor. Yardım almak için uygulama satıcısına başvurun. | Bunlar, uygulama başlatılmadan oluşan genel hata iletilerdir ve başka bir özel neden bulunamamalıdır. Bu, genellikle uygulamanın bozulmuş olduğu veya deponun bozuk olduğu anlamına gelir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . |
| Devam edilemiyor. Uygulama Hatalı biçimli. Yardım almak için uygulama yayımcısına başvurun.<br /><br /> Uygulama doğrulaması başarılı olmadı. Devam edilemiyor.<br /><br /> Uygulama dosyaları alınamıyor. Dağıtımdaki dosyalar bozuk. | Dağıtımdaki bildirim dosyalarından biri sözdizimsel olarak geçerli değil veya karşılık gelen dosyayla mutabık kılınabilecek bir karma içeriyor. Bu hata, bir derleme içine gömülü bildirimin bozuk olduğunu da gösterebilir. Dağıtımınızı yeniden oluşturun ve uygulamanızı yeniden derleyin ya da bildirimlerinizde el ile hataları bulup onarın. |
| Uygulama alınamıyor. Kimlik doğrulama hatası.<br /><br /> Uygulama yüklemesi başarılı olmadı. Sunucudaki uygulama dosyaları bulunamıyor. Yardım için uygulama yayımcısına veya yöneticinize başvurun. | Dağıtımdaki bir veya daha fazla dosya, bunlara erişim izniniz olmadığından indirilemiyor. Bunun nedeni, bir Web sunucusu tarafından döndürülen 403 yasaklanmış bir hata olabilir. bu durum, dağıtımınızdaki dosyalardan biri Web sunucusunun korumalı bir dosya olarak kabul eden bir uzantıyla biterse meydana gelebilir. Ayrıca, bir veya daha fazla uygulama dosyasını içeren bir dizin, erişim için bir Kullanıcı adı ve parola gerektirebilir. |
| Uygulama indirilemiyor. Uygulamada gerekli dosyalar eksik. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Uygulama bildiriminde listelenen bir veya daha fazla dosya sunucuda bulunamıyor. Tüm dağıtımın bağımlı dosyalarını karşıya yükleyip yüklemediğinize emin olun ve yeniden deneyin. |
| Uygulama indirmesi başarılı olmadı. Ağ bağlantınızı denetleyin veya sistem yöneticinize veya ağ hizmeti sağlayıcısına başvurun. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sunucuya ağ bağlantısı kurulamıyor. Sunucunun kullanılabilirliğini ve ağınızın durumunu inceleyin. |
| URLDownloadToCacheFile, HRESULT ' ' ile başarısız oldu \<number> . ' ' İndirilmeye çalışılırken bir hata oluştu \<file> . | Bir Kullanıcı, dağıtım hedef bilgisayarında Internet Explorer Gelişmiş Güvenlik seçeneğini "güvenli ve güvenli olmayan mod arasında değişiklik yaptıysanız uyar" olarak ayarlandıysa ve yüklenmekte olan ClickOnce uygulamasının kurulum URL 'SI güvenli bir siteye (veya tersi) yönlendirilirse, Internet Explorer uyarısı bunu kestiğinden yükleme başarısız olur.<br /><br /> Bu hatayı çözmek için aşağıdaki görevlerden birini yapabilirsiniz:<br /><br /> -Güvenlik seçeneğini temizleyin.<br />-Kurulum URL 'sinin güvenlik modlarını değiştiren bir şekilde yeniden yönlendirilmediğinden emin olun.<br />-Yeniden yönlendirmeyi tamamen kaldırın ve gerçek kurulum URL 'sini işaret edin. |
| Sabit diske yazılırken bir hata oluştu. Diskte yeterli alan yok olabilir. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Bu, uygulamayı depolamak için yeterli disk alanı olduğunu gösterebilir, ancak uygulama dosyalarını sürücüye kaydetmeye çalışırken daha genel bir g/ç hatası da belirtebilir. |
| Uygulama başlatılamıyor. Diskte yeterli kullanılabilir alan yok. | Sabit disk dolu. Alanı temizleyin ve uygulamayı yeniden çalıştırmayı deneyin. |
| Çok fazla dağıtılan etkinleştirme aynı anda yüklenmeye çalışıyor. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aynı anda başlayabilirler farklı uygulama sayısını sınırlar. Bu, yerel hizmette karşı hizmet reddi saldırılarını önlemeye yönelik kötü niyetli saldırılara karşı korunmaya yardımcı olur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; aynı uygulamayı art arda başlatmaya çalışan kullanıcılar, hızlı bir şekilde, uygulamanın yalnızca tek bir örneği ile sona acaktır. |
| Kısayollar ağ üzerinden etkinleştirilemez. | Bir uygulamanın kısayolları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yalnızca yerel sabit diskte başlatılabilir. Uzak bir sunucudaki kısayol dosyasına işaret eden bir URL açılarak başlatılamaz. |
| Uygulama kısmi güvende çevrimiçi çalıştırılamayacak kadar büyük. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Kısmi güvende çalışan bir uygulama, varsayılan olarak 250 MB olan çevrimiçi uygulama kotasının boyutunun yarısından daha büyük olamaz. |

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)