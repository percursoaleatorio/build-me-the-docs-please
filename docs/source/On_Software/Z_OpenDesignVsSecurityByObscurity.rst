Security risks 
--------------

.. Topic:: Security risks

   Security issues are to be considered with more attention. 
   If your software is well written, the publication of the source code 
   should not facilitate security breaches (intrusion by hackers etc.) 
   as the code should not contain passwords, 
   nor sensitive or personal data as names or biometrics, 
   or information on possible back door etc. 
   At the contrary, the Open Source publication of the code 
   should by the time reinforce software security 
   by allowing a wider community to screen it for possible bugs.
   However, if a software is effectively used for critical applications 
   and if the published source code contains serious security flaws, 
   disclosing the code will generate real risks of hacking, 
   at least in a first stage, before bug corrections. 
   Therefore, depending on the sensitive character of the application 
   and the nature of accessed data, 
   a risk assessment is recommended prior to Open Source distribution.

   Source: `What are the risks of publishing software under the EUPL`_

Open design *vs* security by obscurity
--------------------------------------

There is a common preoccupation 
that the use, reuse or development of open source software 
may promote security breaches. 
The alternative being not to disclose the source code, 
so that potential attackers would be unaware of vulnerabilities -  
the so-called 'security by obscurity'.

However, the latter is not applicable when a software system is meant 
to be deployed, managed and (possibly) further developed by different IT teams 
and so there no real control over whom will have access to it.

Furthermore, a well-established software design principle 
establishes that software security should not rely (or presume) 
lack of knowledge from potential attackers. 
The security of a mechanism should not depend on the 
secrecy of its design or implementation
but on the separation of the protection mechanisms 
(e.g. a cryptographic algorithm) 
from the protection keys (e.g. a cryptographic key or password).

In conclusion:

*  'Security by obscurity' can and should be applied to the data.

*  'Open design' can and should be applied to the software.

The following excerpts synthetize these views:

.. topic:: Open design 

   The design should not be secret. 
   
   The [security] mechanisms should not depend on the ignorance of potential attackers, 
   but rather on the possession of specific, more easily protected, keys or passwords. 
   
   This decoupling of protection mechanisms from protection keys 
   permits the mechanisms to be examined by many reviewers 
   without concern that the review may itself compromise the safeguards. 
   
   In addition, any skeptical user may be allowed to convince himself 
   that the system he is about to use is adequate for his purpose.
   
   Finally, it is simply not realistic to attempt to maintain secrecy 
   for any system which receives wide distribution.
   
   Source: [SaSc75]_


.. topic:: Can 'security by obscurity' be a basis for security?

   'Security by Obscurity' can work, but **iff**:
   
   *  Keeping secret actually improves security
   *  You can keep the critical information a secret

   For obscurity itself to give significant security:
   
   *  Keep source secret from all but a few people
   *  Never sell or reveal source to many
   *  Keep binary secret; never sell binary to outsiders
   *  Use software protection mechanisms
   *  Remove software binary before exporting system
   *  Do not allow inputs/outputs of program to be accessible by others 
      (no Internet/web access)

   Source: [Whee12]_
   
   
.. rubric: Citations

.. [Whee12] Wheeler, D. (2012). Open Source Software (OSS or FLOSS) and the U.S. Department of Defense (DoD). 2012-08-15. URL: http://www.dwheeler.com/essays/oss-dod-overview-2012-08-15.ppt
.. [SaSc75] Saltzer, J. H.; Schroeder, M. D. (1975). The protection of information in computer systems. Proceedings of the IEEE. 63(9) :1278-1308 URL: http://www.acsac.org/secshelf/papers/protection_information.pdf

.. links-placeholder

.. _What are the risks of publishing software under the EUPL: https://joinup.ec.europa.eu/software/page/eupl/how-use-eupl