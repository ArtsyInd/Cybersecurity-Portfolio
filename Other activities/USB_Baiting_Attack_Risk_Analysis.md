# USB Baiting Attack: Risk Analysis

## Activity Overview

This activity examines the security risks associated with an unfamiliar USB drive and applies an attacker mindset to understand how USB baiting can be used against an organization.

The scenario focuses on a USB drive found in the parking lot of **Rhetorical Hospital**. The drive contains a mixture of personal and work-related information belonging to **Jorge Bailey, the human resource manager**.

---

## Scenario

A USB drive displaying the hospital's logo is found in the parking lot. Instead of connecting it directly to a normal workstation, the security team uses a workstation with virtualization software to safely investigate the device.

The USB drive contains personal and work-related files, including family and pet photos, a new hire letter, and an employee shift schedule.

This scenario demonstrates why an unfamiliar USB device should be treated as a potential security risk even when its contents do not immediately appear malicious.

---

## 1. Contents

The USB drive contains a mixture of personal and work-related information belonging to Jorge Bailey. The personal files include family and pet photos, while the work-related files include a new hire letter and an employee shift schedule. The combination of personal information and workplace information could reveal details about Jorge, employees, and the hospital.

---

## 2. Attacker Mindset

An attacker could use the personal information to learn more about Jorge and potentially create convincing social-engineering or phishing attempts targeting him or people he knows. The work-related documents could also reveal information about employees and hospital operations. The USB may have been intentionally staged as bait to encourage someone to open the files and potentially connect an infected device to the hospital's network.

---

## 3. Risk Analysis

USB baiting can expose an organization to risks such as malware infection, unauthorized access, data theft, or compromise of sensitive information. Technical controls such as endpoint protection, device controls, restricted USB access, and network segmentation can reduce the impact of a malicious device. Operational controls should include employee awareness training and procedures for reporting and safely handling unknown USB drives. Management should also keep personal and business USB devices separate and establish clear policies for removable media.

---

## 4. Security Controls

### Technical Controls

- Use endpoint security and anti-malware software.
- Restrict or disable USB storage devices where they are not required.
- Use device-control policies to allow only authorized removable media.
- Apply network segmentation to limit the impact of a compromised workstation.
- Keep operating systems and security software updated.
- Use virtualization or isolated analysis environments when investigating unfamiliar devices.

### Operational Controls

- Train employees not to plug unknown USB drives into company computers.
- Establish a process for reporting found or suspicious USB devices to the security team.
- Keep personal and business USB devices separate.
- Require security personnel to investigate unfamiliar removable media in an isolated environment.

### Managerial Controls

- Establish a clear removable-media security policy.
- Define responsibilities for reporting and handling suspicious devices.
- Regularly review USB-device policies and employee awareness.
- Apply security requirements consistently across the organization.

---

## 5. Why the USB Is a Security Risk

The USB drive presents a risk even if the visible files are legitimate. An attacker could intentionally place a USB drive containing attractive or apparently useful information in a location where an employee would find it. The goal could be to persuade the employee to connect the device to a workstation, potentially providing an opportunity for malicious software or unauthorized activity.

The information already present on the drive is also sensitive from a security perspective. Personal and workplace information can help an attacker understand an individual or organization and support targeted social-engineering attempts.

---

## 6. Attacker Mindset Applied

The attacker mindset can be summarized as:

1. **Identify the target** — Jorge, hospital employees, or Rhetorical Hospital.
2. **Determine how the target can be accessed** — through a USB device that an employee may voluntarily connect.
3. **Evaluate the attack vector** — USB baiting provides a physical pathway into a user's workstation.
4. **Consider possible methods** — malicious software, social engineering, credential theft, or unauthorized access could potentially follow from the initial interaction.

This demonstrates that an attack does not always begin with a remote network connection. A physical device can become an entry point into an organization's digital environment.

---

## 7. Recommended Response to an Unknown USB

If an employee finds an unfamiliar USB drive:

1. **Do not plug it into a normal workstation.**
2. **Do not open or execute files from the device.**
3. Report the device to the organization's security or IT team.
4. If investigation is necessary, use an isolated environment such as a dedicated analysis workstation or virtualized environment.
5. Preserve relevant information about where and when the device was found.
6. Follow the organization's removable-media and incident-response procedures.

---

## Conclusion

This activity demonstrates how USB baiting can combine a physical attack vector with social engineering to create a security risk. The USB drive contained both personal and work-related information that could potentially be useful to an attacker, even without malicious code being present. The strongest response is to avoid interacting with unknown USB devices and use a combination of technical controls, employee awareness, removable-media policies, and isolated analysis environments to reduce the risk.
