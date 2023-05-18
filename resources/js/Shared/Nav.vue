<template>
    <nav class="bg-gray-800">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex h-16 items-center justify-between">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <img class="h-8 w-8" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company" />
            </div>
            <div class="hidden md:block">
              <div class="ml-10 flex items-baseline space-x-4">
                <NavLink href="/" :active="$page.component == 'Home'">Home</NavLink>
                <NavLink href="/users" :active="$page.component == 'Users'">Users</NavLink>
                <NavLink href="/settings" :active="$page.component == 'Settings'">Settings</NavLink>
                <span>|</span>
                <a href="/" :active="$page.component == 'Home'">Home</a>
                <a href="/users" :active="$page.component == 'Users'">Users</a>
                <a href="/settings" :active="$page.component == 'Settings'">Settings</a>
              </div>
            </div>
          </div>
          <div class="hidden md:block">
                <div class="ml-4 flex items-center md:ml-6">
                    <div class="relative ml-3">
                        <div>
                            <button type="button" class="flex max-w-xs items-center rounded-full bg-gray-800 text-sm focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800" id="user-menu-button" aria-expanded="false" aria-haspopup="true"  @click="show = !show">
                            <span class="sr-only">Open user menu</span>
                            <img class="h-8 w-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
                            </button>
                        </div>
                        <div v-show="show" class="absolute right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none" role="menu" aria-orientation="vertical" aria-labelledby="user-menu-button" tabindex="-1">
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-0">Your Profile</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-1">Settings</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-2">Sign out</a>
                        </div>
                    </div>
                    <div class="ml-2 min-w-0 flex-auto">
                        <p class="text-sm font-semibold text-white">{{ username }}</p>
                        <p class="mt-0 truncate text-xs text-gray-300">{{ $page.props.auth.email }}</p>
                    </div>
                </div>
            </div>
        </div>
      </div>
    </nav>
</template>

<script>
import NavLink from './NavLink.vue'
export default {
    components: { NavLink },
    data() {
      return {
        show: false,
      };
    },
    computed: {
        username() {
            return this.$page.props.auth.name + "!"
        }
    }
};

</script>
