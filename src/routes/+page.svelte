<script lang="ts">
	import {
		Navbar,
		NavbarBrand,
		NavbarToggler,
		Collapse,
		Nav,
		NavItem,
		NavLink,
		Dropdown,
		DropdownItem,
		DropdownToggle,
		DropdownMenu,
		Icon,
		Styles,
		Container
	} from '@sveltestrap/sveltestrap';

	let isOpen = false;
	enum themeState {
		Auto = 'auto',
		Dark = 'dark',
		Light = 'light'
	}
	let theme = themeState.Auto;
	function handleUpdate(event: any) {
		isOpen = event.detail.isOpen;
	}
</script>

<Styles {theme} />

<Navbar color="primary-subtle" expand="md" container="md">
	<NavbarBrand href="/">My Svelte App</NavbarBrand>
	<NavbarToggler on:click={() => (isOpen = !isOpen)} />
	<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
		<Nav class="ms-auto" navbar>
			<NavItem>
				<NavLink href="#components/">Components</NavLink>
			</NavItem>
			<NavItem>
				<NavLink href="https://github.com/sveltestrap/sveltestrap">GitHub</NavLink>
			</NavItem>
			<Dropdown nav inNavbar>
				<DropdownToggle nav caret>Theme</DropdownToggle>
				<DropdownMenu end>
					<DropdownItem
						active={theme === themeState.Light}
						on:click={() => (theme = themeState.Light)}><Icon name="sun-fill" /> light</DropdownItem
					>
					<DropdownItem
						active={theme === themeState.Dark}
						on:click={() => (theme = themeState.Dark)}
						><Icon name="moon-stars-fill" /> dark</DropdownItem
					>
					<DropdownItem
						active={theme === themeState.Auto}
						on:click={() => (theme = themeState.Auto)}
						><Icon name="circle-half" /> auto</DropdownItem
					>
				</DropdownMenu>
			</Dropdown>
		</Nav>
	</Collapse>
</Navbar>

<Container md>
	<h1>Welcome to SvelteKit</h1>
	<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
</Container>
