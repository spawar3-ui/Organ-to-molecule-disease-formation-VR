# Organ to Molecule VR

**A VR journey from a diseased heart to a statin binding its target enzyme.**

![Demo GIF](docs/demo.gif)
<!-- Replace with your demo GIF or a link to your 60-90 second demo video -->

> Status: prototype in active development (Unity + OpenXR, built for Meta Quest).

---

## The problem

Patients and students often understand heart disease as "a blocked artery" but not why the blockage forms or how a drug like a statin treats it. Textbooks present the organ, cell, and molecular levels in separate chapters, so the connection between them never gets made.

## The idea

This project lets users travel through all of these scales in one continuous VR experience, manipulate a drug molecule, and see its effect on the whole organ.

Grab-and-rotate anatomy is only the entry point. The learning comes from **connecting scales** and from **causing the effect yourself** by placing the drug.

## The experience

1. **Organ:** Grab and rotate the heart. One coronary artery is narrowed.
2. **Tissue:** Zoom into the artery cross-section and see plaque restricting blood flow.
3. **Cell:** Zoom into the artery wall and see LDL cholesterol entering and immune cells turning into foam cells that build up plaque.
4. **Molecule:** Find the liver enzyme that produces cholesterol (HMG-CoA reductase). Pick up a statin molecule and place it in the enzyme's active site.
5. **Zoom back out:** With the drug in place, cholesterol production drops and plaque growth stops. See the full chain from molecule to organ.

**Key takeaway:** a statin acts in the liver, at a single enzyme, and that small molecular change shows up as a healthier artery in the heart.

## Features

- [ ] Grabbable, rotatable heart model
- [ ] Seamless zoom between organ, tissue, cell, and molecule scales
- [ ] Artery cross-section with plaque
- [ ] Cell-level scene (LDL, foam cells)
- [ ] Real protein structure from the Protein Data Bank
- [ ] Grab-and-place statin interaction with drug on/off toggle
- [ ] Pre- and post-experience quiz
- [ ] Small user study (see [Evaluation](#evaluation))

<!-- Tick boxes as you finish each feature -->

## Why this is different

Molecular VR tools (such as Nanome and ChimeraX) and VR anatomy apps already exist. This project combines them into one guided story that links disease at the organ level to its cause and treatment at the molecular level, and lets the user trigger the effect.

## A reusable framework

The structure is disease-agnostic: organ, then cell, then molecule, then zoom back out. Statins are the first module. Other modules could reuse the same zoom and drug-interaction system:

| Module | Organ | Cell level | Molecule |
|---|---|---|---|
| Heart disease (this prototype) | Heart and narrowed artery | Foam cells, plaque | Statin in HMG-CoA reductase |
| Type 2 diabetes (future) | Pancreas | Beta cells, insulin resistance | Insulin receptor or metformin |
| Cancer (future) | Tumor | Dividing cancer cells | Targeted drug on a growth-signal protein |

Disease-specific content (models, text, quiz) is kept separate from the shared zoom and interaction code so a new module can be added without rewriting the core.

## Tech stack

- **Engine:** Unity (version listed in `ProjectSettings/ProjectVersion.txt`)
- **XR:** XR Interaction Toolkit, XR Plugin Management, OpenXR
- **Target device:** Meta Quest (Android build)
- **Medical imaging:** 3D Slicer, used to segment cardiac structures from a CT scan
- **Molecular data:** Protein Data Bank structures, prepared as meshes with UCSF ChimeraX

## Getting started

### Requirements

- Unity (matching the version above) with **Android Build Support** installed
- A Meta Quest headset with Developer Mode enabled
- Git (and Git LFS if large model files are tracked)

### Run it

1. Clone the repository:
   ```bash
   git clone https://github.com/spawar3-ui/Organ-to-molecule-disease-formation-VR.git
   ```
2. Open Unity Hub, choose **Add > Add project from disk**, and select the cloned folder. The first open takes a few minutes while Unity regenerates the `Library` folder.
3. Open the main scene (path: `Assets/Scenes/...`).
4. To test on a Mac without a headset, use the **XR Device Simulator** from the XR Interaction Toolkit samples.
5. To run on a Quest: connect it by USB-C, accept the debugging prompt, then use **File > Build and Run** with the platform set to Android.

> Note: Quest Link (live preview over a cable) is not available on macOS, so builds are installed directly on the headset.

## Project structure

```
Assets/
  Scenes/            Unity scenes
  Scripts/
    Core/            Zoom system, grab and place logic (shared across modules)
    Modules/Statin/  Content-specific scripts for the heart/statin module
  Models/            Heart, artery, cell, and molecule meshes
  Materials/
  UI/                Labels and quiz
Packages/
ProjectSettings/
docs/                Demo media and write-up
```

<!-- Update this to match your real folder layout -->

## Evaluation

A small informal study compares learning outcomes after using this VR experience versus a 2D alternative.

- **Participants:** TBD
- **Method:** short quiz before and after, VR group versus 2D group
- **Results:** TBD

Results will be reported honestly, including the small sample size.

## Science and limitations

- The models are simplified illustrations for teaching, not clinical tools.
- This is not a medical device and should not be used for diagnosis or treatment decisions.
- Cell-level and molecular scenes are stylized. Science review by: TBD.

## Data and credits

- **Heart anatomy:** segmented from the CTACardio sample dataset in 3D Slicer (or replace with the premade model you used and credit its source and license).
- **Protein structure:** Protein Data Bank, entry TBD. Please cite the original authors of the structure.
- **Other assets:** list any third-party models, textures, or sounds with their licenses here.

No patient-identifiable scan data is included in this repository.

## Roadmap

- Add a second module (for example, type 2 diabetes) to demonstrate the framework
- Voice or text guidance at each scale
- Larger user study

## Author

Built by [spawar3-ui](https://github.com/spawar3-ui) as a portfolio project.

## License

TBD. Consider adding a license through GitHub (for example MIT for code) and check the licenses of any third-party assets.
