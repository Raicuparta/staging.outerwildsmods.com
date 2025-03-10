<script lang="ts">
	import CtaButton from '$lib/components/button/cta-button.svelte';
	import PageContainer from '$lib/components/page-container.svelte';
	import PageSectionImage from '$lib/components/page-section/page-section-image.svelte';
	import PageSection from '$lib/components/page-section/page-section.svelte';
	import WindowsIcon from '$lib/components/windows-icon.svelte';
	import { websiteUrl } from '$lib/helpers/constants';

	const repoUrl = 'https://github.com/ow-mods/ow-mod-manager';
	const downloadUrl = `${repoUrl}/releases/latest/download`;
	const installerDownloadUrl = `${downloadUrl}/OuterWildsModManager-Installer.exe`;
	const portableDownloadUrl = `${downloadUrl}/OuterWildsModManager-Portable.zip`;
</script>

<PageContainer
	title="Outer Wilds Mod Manager - Download Windows app"
	description="Download, install, and manage Outer Wilds mods using the Outer Wilds Mod Manager for Windows."
	imageUrl="{websiteUrl}/images/mod-manager.webp"
	imageWidth={887}
	imageHeight={416}
>
	<PageSection title="Outer Wilds Mod Manager" id="mod-manager" isNarrow>
		<div>
			<PageSectionImage imageUrl="/images/mod-manager.webp" title="Outer Wilds Mod Manager" />
		</div>
		<div class="my-4">
			<CtaButton href={installerDownloadUrl} rel="noopener noreferrer">
				<WindowsIcon />
				Download the Outer Wilds Mod Manager for Windows
			</CtaButton>
		</div>
		<p>
			or{' '}
			<a class="link" href={portableDownloadUrl} rel="noopener noreferrer">
				download the portable version instead
			</a>
		</p>
		<p class="mt-4">For all your modding needs! With access to features such as:</p>
		<ul class="my-4">
			<li>Downloading mods;</li>
			<li>Updating mods;</li>
			<li>Enabling / disabling mods;</li>
			<li>Looking at all the great mods you have;</li>
			<li>Running the game with mods enabled.</li>
		</ul>
		<p>
			It also lets you install / update the{' '}
			<a class="link" href="/mods/owml">Outer Wilds Mod Loader</a> from within the app, so you don't
			need to deal with that yourself.
		</p>
	</PageSection>
	<PageSection title="How do I use this?" id="how-to-use" isNarrow>
		<ul>
			<li>Download the Outer Wilds Mod Manager installer;</li>
			<li>Run the downloaded .exe (you might need to ignore some Chrome / Windows warnings);</li>
			<li>The Mod Manager should start automatically;</li>
			<li>
				Shortcuts are added to desktop and start menu, use them next time you want to run the
				manager;
			</li>
			<li>Install OWML;</li>
			<li>Install any mods you want;</li>
			<li>Press the big green button that says "Start Game";</li>
			<li>You won't believe what happens next.</li>
		</ul>
	</PageSection>
	<PageSection title="How do I uninstall it?" id="uninstall" isNarrow>
		<p>
			First, remember that uninstalling the Mod Manager won't uninstall your mods. Make sure to
			remove all mods and run the game once before uninstalling.
		</p>
		<p>
			You can uninstall the Mod Manager by searching for "Add or remove programs" in the start menu
			(or in the control panel), and then finding Outer Wilds Mod Manager in the list.
		</p>
		<p class="mt-4">To revert the game to its original state, verify the game files integrity:</p>
		<ul>
			<li>
				<b>Steam</b>: Library &gt; Right-click Outer Wilds &gt; Properties &gt; Local Files &gt;
				Verify integrity of game files.
			</li>
			<li>
				<b>Epic</b>: Library &gt; Click three dots under Outer Wilds &gt; Verify.
			</li>
		</ul>
	</PageSection>
	<PageSection title="More information" id="more-info" isNarrow>
		<p>
			For more information, check the{' '}
			<a
				class="link"
				target="_blank"
				rel="noopener noreferrer"
				href="https://github.com/ow-mods/ow-mod-manager#readme"
			>
				readme on GitHub
			</a>
		</p>
	</PageSection>
</PageContainer>
