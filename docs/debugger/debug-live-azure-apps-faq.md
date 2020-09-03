---
title: Anlık görüntü hata ayıklaması hakkında SSS | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e0d8839daac2d470f4275257bfcfbc83fc7a62f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911400"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 'da anlık görüntü hata ayıklaması için sık sorulan sorular

Snapshot Debugger kullanarak canlı Azure uygulamalarında hata ayıklarken oluşabilecek soruların bir listesi aşağıda verilmiştir.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Anlık görüntü alma performans maliyeti nedir?

Snapshot Debugger uygulamanızın bir anlık görüntüsünü yakaladığında, uygulamanın sürecini çatallandırın ve ele geçirilen kopyayı askıya alır. Bir anlık görüntüde hata ayıkladığınızda, işlemin yürütülen kopyasına göre hata ayıklaması yapılır. Bu işlem yalnızca 10-20 milisaniye sürer ancak uygulamanın tam yığınını kopyalamaz. Bunun yerine, yalnızca sayfa tablosunu kopyalar ve yazma üzerine kopyalamak için sayfaları ayarlar. Uygulamanızın yığındaki bazı nesneler değiştiğinde ilgili sayfaları kopyalanır. Bu, her anlık görüntünün küçük bir bellek içi maliyeti vardır (çoğu uygulama için yüzlerce kilobayt sırasıyla).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Ölçeği genişletilmiş bir Azure App Service (uygulamamın birden çok örneği) varsa ne olur?

Uygulamanızın birden çok örneğine sahip olduğunuzda, anlık görüntü noktaları her tek örneğe uygulanır. Yalnızca belirtilen koşullara uyan ilk anlık görüntü noktası bir anlık görüntü oluşturur. Birden çok anlık görüntü noktanız varsa, sonraki anlık görüntüler ilk anlık görüntüyü oluşturan örnekten gelir. Çıkış penceresine gönderilen günlüğe kaydetme noktaları 'ler yalnızca bir örnekten gelen iletileri gösterir, ancak uygulama günlüklerine gönderilen günlüğe kaydetme noktaları her örnekten ileti gönderir.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Snapshot Debugger sembolleri nasıl yükleyebilir?

Snapshot Debugger, uygulamanız için yerel ya da Azure App Service dağıtılan eşleşen simgelere sahip olmanızı gerektirir. (Embedded pdb 'leri Şu anda desteklenmiyor.) Snapshot Debugger, Azure App Service sembolleri otomatik olarak indirir. Visual Studio 2017 sürüm 15,2 ' den başlayarak, Azure App Service dağıtım, uygulamanızın sembollerini de dağıtır.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Snapshot Debugger uygulamamın yayın Derlemeleriyle mi çalışıyor?

Evet-Snapshot Debugger yayın yapılarına karşı çalışmak üzere tasarlanmıştır. Bir anlık görüntü noktası bir işleve yerleştirildiğinde, işlev bir hata ayıklama sürümüne yeniden derlenir, bunu hata ayıklanabilir yapar. Snapshot Debugger durdurulduğunda, işlev yayın derlemesinin sürümüne döndürülür.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Günlüğe kaydetme noktaları, üretim uygulamamda yan etkilere neden olabilir mi?

Hayır-uygulamanıza eklediğiniz herhangi bir günlük iletisi neredeyse değerlendirilir. Uygulamanızda herhangi bir yan etkiye neden olamaz. Ancak, bazı yerel özellikler logpoints ile erişilebilir olmayabilir.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Sunucum yükleme altındaysa Snapshot Debugger çalışır mi?

Evet, anlık görüntü hata ayıklaması yük altındaki sunucular için çalışabilir. Snapshot Debugger, sunucunuzda düşük miktarda boş bellek olduğu durumlarda, anlık görüntüleri kısıtlar ve yakalamaz.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Snapshot Debugger Nasıl yaparım? kaldırmak istiyor musunuz?

App Service Snapshot Debugger site uzantısını aşağıdaki adımlarla kaldırabilirsiniz:

1. App Service, Visual Studio veya Azure portal bulut Gezgini aracılığıyla kapatın.
1. App Service kudu sitenize (yani, yourappservice) gidin.** SCM**. azurewebsites.net) ve **site uzantılarına**gidin.
1. Kaldırmak için Snapshot Debugger site uzantısında X öğesine tıklayın.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Snapshot Debugger oturumu sırasında bağlantı noktaları neden açıldı?

Snapshot Debugger, Azure 'da alınan anlık görüntülerde hata ayıklamak için bir bağlantı noktası kümesi açması gerekir, bunlar uzaktan hata ayıklama için gereken bağlantı noktalarıyla aynıdır. [Bağlantı noktalarının listesini buradan bulabilirsiniz](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Nasıl yaparım? uzaktan hata ayıklayıcı uzantısını devre dışı bırakmak istiyor musunuz?

Uygulama Hizmetleri için:
1. App Service için Azure portal uzaktan hata ayıklayıcı uzantısını devre dışı bırakın.
2. Uygulama *ayarlarını* > uygulama hizmeti kaynak dikey penceresini > Azure Portal
3. *Hata ayıklama* bölümüne gidin ve *Uzaktan hata ayıklama*için *kapalı* düğmesine tıklayın.

AKS için:
1. [Docker görüntülerinde Visual Studio Snapshot Debugger](https://github.com/Microsoft/vssnapshotdebugger-docker)karşılık gelen bölümleri kaldırmak Için Dockerfile dosyanızı güncelleştirin.
2. Değiştirilen Docker görüntüsünü yeniden derleyin ve yeniden dağıtın.

Sanal makine/sanal makine ölçek kümeleri için uzaktan hata ayıklayıcı uzantısı, sertifikalar, Anahtar kasaları ve gelen NAT havuzlarını aşağıdaki gibi kaldırın:

1. Uzaktan hata ayıklayıcı uzantısını kaldır

   Sanal makineler ve sanal makine ölçek kümeleri için uzak hata ayıklayıcıyı devre dışı bırakmak için çeşitli yollar vardır:

      - Bulut Gezgini aracılığıyla uzaktan hata ayıklayıcıyı devre dışı bırakma

         - Cloud Explorer > hata ayıklamayı devre dışı bırak (bulut Gezgini 'nde sanal makine ölçek kümesi için hata ayıklamayı devre dışı bırakma yok) >.

      - Uzaktan hata ayıklayıcıyı PowerShell betikleri/cmdlet 'Leriyle devre dışı bırakma

         Sanal makine için:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Sanal Makine Ölçek Kümeleri için:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Azure portal aracılığıyla uzaktan hata ayıklayıcıyı devre dışı bırakın
         - Azure portal sanal makineniz/sanal makine ölçek kümeleri kaynak dikey penceresi > uzantıları >
         - Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger uzantısını kaldır

         > [!NOTE]
         > Sanal Makine Ölçek Kümeleri-Portal DebuggerListener bağlantı noktalarının kaldırılmasına izin vermez. Azure PowerShell kullanmanız gerekir. Ayrıntılar için aşağıya bakın.

2. Sertifikaları ve Azure Keykasasını kaldırma

   Sanal makine veya sanal makine ölçek kümeleri için uzaktan hata ayıklayıcı uzantısı yüklenirken, Azure sanal makinesi/sanal makine ölçek kümeleri kaynaklarıyla VS istemcisinin kimliğini doğrulamak için hem istemci hem de sunucu sertifikaları oluşturulur.

   - Istemci sertifikası

      Bu sertifika, CERT:/CurrentUser/My/öğesinde bulunan kendinden imzalı bir sertifikadır.

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Bu sertifikayı makinenizden kaldırmanın bir yolu PowerShell ile

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Sunucu sertifikası
      - Karşılık gelen sunucu sertifikası parmak izi, Azure Keykasasında gizli dizi olarak dağıtılır. VS, sanal makine veya sanal makine ölçek kümeleri kaynağına karşılık gelen bölgede MSVSAZ * önekiyle bir Keykasası bulmayı veya oluşturmayı dener. Bu bölgeye dağıtılan tüm sanal makine veya sanal makine ölçek kümeleri kaynakları aynı anahtar kasasını paylaşır.
      - Sunucu sertifikası parmak izi gizli anahtarını silmek için Azure portal gidin ve parolanızı barındıran bölgede MSVSAZ * Keykasasını bulun. Etiketlenmesi gereken gizli anahtarı sil `remotedebugcert<<ResourceName>>`
      - Ayrıca, PowerShell aracılığıyla kaynağından sunucu parolasını da silmeniz gerekir.

      Sanal makineler için:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Sanal Makine Ölçek Kümeleri için:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Tüm DebuggerListener gelen NAT havuzlarını Kaldır (yalnızca sanal makine ölçek kümesi)

   Uzaktan hata ayıklayıcı, scaleset 'in yük dengeleyicisine uygulanan bir DebuggerListener 'ın bağlantılı NAT havuzlarını tanıtır.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Snapshot Debugger devre dışı Nasıl yaparım??

App Service için:
1. App Service için Azure portal aracılığıyla Snapshot Debugger devre dışı bırakın.
2. Uygulama *ayarlarını* > uygulama hizmeti kaynak dikey penceresini > Azure Portal
3. Azure portal aşağıdaki uygulama ayarlarını silin ve değişikliklerinizi kaydedin.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Uygulama ayarlarında yapılan değişiklikler, uygulamanın yeniden başlatılmasını başlatır. Uygulama ayarları hakkında daha fazla bilgi için, [Azure portal App Service uygulama yapılandırma](/azure/app-service/web-sites-configure)konusuna bakın.

AKS için:
1. [Docker görüntülerinde Visual Studio Snapshot Debugger](https://github.com/Microsoft/vssnapshotdebugger-docker)karşılık gelen bölümleri kaldırmak Için Dockerfile dosyanızı güncelleştirin.
2. Değiştirilen Docker görüntüsünü yeniden derleyin ve yeniden dağıtın.

Sanal makine/sanal makine ölçek kümeleri için:

Snapshot Debugger devre dışı bırakmak için birkaç yol vardır:
- Bulut Gezgini > sanal makineniz/sanal makine ölçek kümesi kaynağınız > tanılamayı devre dışı bırak

- Azure portal > sanal makineniz/sanal makine ölçek kümesi kaynak dikey penceresi > uzantıları > Microsoft. Insights. VMDiagnosticsSettings uzantısını kaldır

- [Az PowerShell](/powershell/azure/overview) 'Den PowerShell cmdlet 'leri

   Sanal makine:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Sanal Makine Ölçek Kümeleri:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure sanal makine ölçek kümelerinde hata ayıkla](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure Kubernetes hatalarını ayıklama](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hata ayıklaması için sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md)
