#CONTENTS 


   ##1.Introduction of Trustzone
      ->TrustZone provides hardware isolation while inteaction between application code and firware 
      ->TrustZone is a security developed by a ARM
	  ->Its provides a trusted exicution environment(TEE) for secure applications

    **1.1 Separation of environments 
      ->TrustZone dived system into two types 
        i.secure world :- its runs trusted application
        ii.non secire world :- its runs untrusted application

    **1.2 Secure boot 
      ->TrustZone supports secure boot processes 
      ->ensuring that only verified and authenticated software can run on the device from the start.

    **1.3 Hardware isolation
      ->making it difficult for malicious software in the normal world to access sensitive data in the secure world.

    **1.4 Resource sharing 
      -> TrustZone enables secure access to shared resources, allowing secure and normal applications to  coexist while maintaining security.

    **1.5 Cryphography operation 
      ->hardware acceleration for cryptographic operations, enhancing performance for security-sensitive tasks.


   ##2.What is Trusted Firmware-M

   ##3.Configuration

    **3.1 Firmware framework model
       ->inter_process communication(IPC)
       ->sucure function (SFN)models

    **3.2 isolation process
     3.2.1 Level 1 isolation
        ->this is basic separation suitable for low-security needs. 
     3.2.2 Level 2 isolation
        ->enhances security through additional controls and features.
     3.2.3 Level 3 isolation
       -> provides comprehensive isolation with advanced protections for high-security environments.

    **3.3 profiles
    types are differenciated based on the framework,isolation,internal trusted storage,protected storage ,Cryptosymatic ,secure boot,initial attention,firmware update.
       3.3.1 default
        ->supported header files :-crypto_config_default.h,tfm_mbedcrypto_config_default.h.
       3.3.2 small
        ->supported header files :- crypto_config_profile_small.h,tfm_mbedcrypto_config_profile_small.h.
       3.3.3 medium ARoT-less
        ->supported header files :-crypto_config_profile_medium.h,tfm_mbedcrypto_config_profile_medium.h.
       3.3.4 medium
        ->supported header files :-crypto_config_profile_medium.h,tfm_mbedcrypto_config_profile_medium.h.
       3.3.5 large
        ->supported header files :-crypto_config_profile_large.h,tfm_mbedcrypto_config_profile_large.h.
  
   ##4.interface mechanism
        ->the actual interface between Secure and Non-secure program images are reduced to a few   interface calls based on the PSA Firmware Framework-M (FF-M) specification. As a result, when creating a Non-secure software project that utilizes the Secure APIs, the project needs to include a few C files to handle the redirection of secure API calls
       ->accessin links for c files  :- 
        i. https://git.trustedfirmware.org/TF-M/trusted-firmware-m.git/tree/interface/src
        ii. https://git.trustedfirmware.org/TF-M/trusted-firmware-m.git/tree/interface/include  

    **4.1 Secure API interface mechanism
        -> The first instruction in the Secure API being called must be an SG (Secure Gateway) 
        instruction.
        -> The address of the first instruction in the Secure API being called must be marked as Non secure Callable (NSC).
        -> As in normal secure codes, the address of the Secure API must be executable and accessible 
        under the permission of the Secure MPU.
        ->The definition of NSC region(s) is based on the address configuration settings.
          i.Security Attribution Unit (SAU)
          ii.Implementation Defined Attribution Unit (IDAU) 

    **4.2 Non secure API interface mechanism
        ->
        ->
        ->
   8.OS interface
   9.Secure boot support
   10.Resources