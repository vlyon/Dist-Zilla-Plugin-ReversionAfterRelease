# NAME

Dist::Zilla::Plugin::ReversionAfterRelease - Bump and reversion after distribution release

# SYNOPSIS

    [VersionFromModule]
    [CopyFilesFromBuild]
    copy = Changes
    
    [UploadToCPAN]
    
    ; commit source files as of "dzil release" with any
    ; allowable modifications (e.g Changes)
    [Git::Commit / Commit_This_Release] ; commit files/Changes (as released)
    commit_msg = Release %v
    
    ; tag as of "dzil release"
    [Git::Tag]
    
    ; update Changes with timestamp of release
    [NextRelease]
    
    [ReversionAfterRelease]
    
    ; commit source files after modification
    [Git::Commit / Commit_Next_Version] ; commit Changes/version (for new dev)
    allow_dirty =
    allow_dirty_match =
    commit_msg = Bump Version to %v

# DESCRIPTION

This Dist::Zilla plugin will bump the version of your module _after_ a successful release.

Similar to [BumpVersionAfterRelease](https://metacpan.org/pod/Dist::Zilla::Plugin::BumpVersionAfterRelease) but uses the more permisable reversioning from [ReversionOnRelease](https://metacpan.org/pod/Dist::Zilla::Plugin::ReversionOnRelease).

# SEE ALSO

Core Dist::Zilla plugins:
[ReversionOnRelease](https://metacpan.org/pod/Dist::Zilla::Plugin::ReversionOnRelease),
[BumpVersionAfterRelease](https://metacpan.org/pod/Dist::Zilla::Plugin::BumpVersionAfterRelease).

Dist::Zilla roles:
[AfterRelease](https://metacpan.org/pod/Dist::Zilla::Plugin::AfterRelease),
[FileMunger](https://metacpan.org/pod/Dist::Zilla::Role::FileMunger).

# AUTHOR

Vernon Lyon <vlyon@cpan.org>

# COPYRIGHT

Copyright 2018 Vernon Lyon

# LICENSE

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.
