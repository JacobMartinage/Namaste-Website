<script>
    export let isOpen = false;
    export let onClose;
</script>

<style>
    .modal-backdrop {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.7);
        z-index: 1001;
        display: flex;
        justify-content: center;
        align-items: start;
        overflow-y: auto;
        padding: 1rem 0;
    }

    .modal-content {
        background: white;
        padding: 0.5rem;
        border-radius: 8px;
        position: relative;
        max-width: 75%;
        margin: 0 auto;
    }

    .close-button {
        position: fixed;
        top: 1rem;
        right: 1rem;
        background: rgba(222, 120, 65, 0.9);
        border: none;
        color: white;
        padding: 1rem 2rem;
        border-radius: 4px;
        cursor: pointer;
        z-index: 1002;
        font-size: 1.2rem;
        font-weight: bold;
    }

    .close-button:hover {
        background: rgba(222, 120, 65, 1);
    }

    img {
        width: 100%;
        height: auto;
        margin-bottom: 0.5rem;
    }

    @media (max-width: 768px) {
        .modal-content {
            max-width: 95%;
        }
    }
</style>

{#if isOpen}
    <div class="modal-backdrop" on:click|self={onClose}>
        <button class="close-button" on:click={onClose}>Close</button>
        <div class="modal-content">
            <img src='namaste-menu-update-july-2025-01.png' alt='page 1'>
            <img src='namaste-menu-update-july-2025-02.png' alt='page 2'>
            <img src='namaste-menu-update-july-2025-03.png' alt='page 3'>
            <img src='namaste-menu-update-july-2025-04.png' alt='page 4'>
            <img src='namaste-menu-update-july-2025-05.png' alt='page 5'>
            <img src='namaste-menu-update-july-2025-06.png' alt='page 6'>
            <img src='namaste-menu-update-july-2025-07.png' alt='page 7'>
            <img src='namaste-menu-update-july-2025-08.png' alt='page 8'>
            <img src='namaste-menu-update-july-2025-09.png' alt='page 9'>
            <img src='namaste-menu-update-july-2025-10.png' alt='page 10'>
            <img src='namaste-drinks-menu-1.png' alt='page 11'>
            <img src='namaste-drinks-menu-2.png' alt='page 12'>

        </div>
    </div>
{/if} 